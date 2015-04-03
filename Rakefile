# == Dependencies ==============================================================

require 'rake'

# == Configuration =============================================================

# Set "rake watch" as default task
task :default => :deploy

# == Helpers ===================================================================

# Execute a system command
def execute(command)
  system "#{command}"
end

# == Tasks =====================================================================

# rake deploy
desc "Deploy the site to a remote git repo"
task :deploy do
    system "git add -A"
    execute("git commit -m \'publication\'")
    execute("git push")
end
