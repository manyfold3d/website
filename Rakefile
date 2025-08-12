require 'dotenv'
Dotenv.load

require 'octokit'

task :download_release_notes do
  client = Octokit::Client.new(:access_token => ENV.fetch("GITHUB_ACCESS_TOKEN"))
  releases = client.releases("manyfold3d/manyfold")
  releases.each do |release|
    File.open("_posts/#{release.published_at.strftime("%F")}-release-#{release.name.gsub('.','-')}.md", "w") do |f|
      f.puts <<-EOF
---
title: Release #{release.name}
date: #{release.published_at}
---
#{fix_links release.body}

See the original release on GitHub: [#{release.name}](#{release.html_url})
EOF
    end
  end
end

def fix_links(markdown)
  markdown.gsub!(/https:\/\/github.com\/([\w\/]+)\/pull\/([0-9]+)/, "[#\\2](https://github.com/\\1/pull/\\2)")
  markdown.gsub!(/(\s)@(\w+)(\s)/, "\\1[@\\2](https://github.com/\\2)\\3")
  markdown.gsub!(/https:\/\/github.com\/([\w\/]+)\/compare\/([\w\.]+)/, "[\\2](https://github.com/\\1/compare/\\2)")
  markdown
end
