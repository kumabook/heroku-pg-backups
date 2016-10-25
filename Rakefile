require "pgbackups-archive"
require "faraday"
require "uri"

task :default do
  begin
    time = Time.now.strftime('%Y-%m-%d %H:%M:%S')
    puts 'pg backups and upload it to s3'
    notify_slack "Start archving backup: #{time}"
    PgbackupsArchive::Job.call
    notify_slack "Successfully archiving backup and save it on s3: #{time}"
    puts 'completed!'
  rescue => e
    puts "Failed to backup"
    notify_slack("Failed to backup")
    p e
  end
end

def notify_slack(text)
  uri = URI.parse(ENV["SLACK_URL"])
  conn = Faraday.new(:url => "#{uri.scheme}://#{uri.host}") do |faraday|
    faraday.request  :url_encoded
    faraday.response :logger
    faraday.adapter  Faraday.default_adapter
  end

  conn.post do |req|
    req.url uri.path
    req.headers['Content-Type'] = 'application/json'
    req.body = "{ \"text\": \"#{text}\" }"
  end

end
