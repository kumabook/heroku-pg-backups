require "pgbackups-archive"
require "faraday"
require "uri"

task :default do
  puts 'pg backups and upload it to s3'
  PgbackupsArchive::Job.call
  uri = URI.parse(ENV["SLACK_URL"])
  conn = Faraday.new(:url => "#{uri.scheme}://#{uri.host}") do |faraday|
    faraday.request  :url_encoded
    faraday.response :logger
    faraday.adapter  Faraday.default_adapter
  end

  conn.post do |req|
    req.url uri.path
    req.headers['Content-Type'] = 'application/json'
    text     = "Successfully backup and save it on s3: #{Time.now.strftime('%Y-%m-%d %H:%M:%S')}"
    req.body = "{ \"text\": \"#{text}\" }"
  end

  puts 'completed!'
end
