require 'bundler'
require 'fileutils'
require 'tmpdir'

Bundler.require

task :default => :groonga

GROONGA_VERSION = '2.0.9'

desc 'Build groonga'
task :groonga do
  uploader = GithubDownloads::Uploader.new
  uploader.authorize

  source_url = "http://packages.groonga.org/source/groonga/groonga-#{GROONGA_VERSION}.tar.gz"

  Dir.mktmpdir('groonga-') do |tmpdir|
    target_filename = "groonga-#{GROONGA_VERSION}.tgz"

    # build
    Dir.chdir(tmpdir) do |dir|
      sh "curl #{source_url} -s -o - | tar zxf -"
      sh "vulcan build -v -o #{target_filename} --prefix /app/vendor/groonga --source groonga-#{GROONGA_VERSION}"

    end
    built_binary_path = File.join(tmpdir, "groonga-#{GROONGA_VERSION}.tgz")

    # upload it to github
    puts "Uploading #{built_binary_path}"
    uploader.upload_file(target_filename, "groonga #{GROONGA_VERSION}", built_binary_path)
  end
end
