require 'fileutils'
require 'tmpdir'

task :default => :groonga

GROONGA_VERSION = '2.0.8'

desc 'Build groonga'
task :groonga do
  source_url = "http://packages.groonga.org/source/groonga/groonga-#{GROONGA_VERSION}.tar.gz"

  built_binary = nil
  Dir.mktmpdir('groonga-') do |tmpdir|
    Dir.chdir(tmpdir) do |dir|
      sh "curl #{source_url} -s -o - | tar zxf -"
      sh "vulcan build -v -o groonga-#{GROONGA_VERSION}.tgz --prefix /app/vendor/groonga --source groonga-#{GROONGA_VERSION}"

      built_binary = File.join(tmpdir, "groonga-#{GROONGA_VERSION}.tgz")
    end

    FileUtils.cp(built_binary, '.')
    # TODO upload it to github
  end
end
