# == Dependencies ==============================================================

require 'rake'
require 'yaml'
require 'fileutils'
require 'rbconfig'

# == Configuration =============================================================

# Set "rake watch" as default task
task :default => :deploy

# == Helpers ===================================================================

# Execute a system command
def execute(command)
  system "#{command}"
end

# == Tasks =====================================================================

# rake build
desc "Build the site"
task :build do
  execute("jekyll build")
end

# rake deploy
desc "Deploy the site to a remote git repo"
task :deploy do
    execute("git add -A")
    execute("git commit -m \'publication\'")
    execute("git push")
end


# rake transfer
desc "Transfer the site (remote server or a local git repo)"
task :transfer do
  command = CONFIG["transfer"]["command"]
  source = CONFIG["transfer"]["source"]
  destination = CONFIG["transfer"]["destination"]
  settings = CONFIG["transfer"]["settings"]
  if command.nil? or command.empty?
    raise "Please choose a file transfer command."
  elsif command == "robocopy"
    Rake::Task[:build].invoke
    execute("robocopy #{source} #{destination} #{settings}")
    puts "Your site was transfered."
  elsif command == "rsync"
    Rake::Task[:build].invoke
    execute("rsync #{settings} #{source} #{destination}")
    puts "Your site was transfered."
  else
    raise "#{command} isn't a valid file transfer command."
  end
end
