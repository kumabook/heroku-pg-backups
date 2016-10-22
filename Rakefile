require "pgbackups-archive"

task :default do
  puts 'pg backups and upload it to s3'
  PgbackupsArchive::Job.call
  puts 'completed!'
end
