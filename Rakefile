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
layout: post
excerpt_separator: "\n\n"
---
#{fix_links release.body}

See the original release on GitHub: [#{release.name}](#{release.html_url})
EOF
    end
  end
end

def fix_links(markdown)
  markdown.gsub!(/https:\/\/github.com\/([\w\/]+)\/pull\/([0-9]+)/, "[#\\2](https://github.com/\\1/pull/\\2)")
  markdown.gsub!(/@(\w+)/, "[@\\1](https://github.com/\\1)")
  markdown.gsub!(/https:\/\/github.com\/([\w\/]+)\/compare\/([\w\.]+)/, "[\\2](https://github.com/\\1/compare/\\2)")
  markdown
end

task :generate_wsg_checklist do
  json = JSON.parse(Net::HTTP.get(URI.parse("https://w3c.github.io/sustyweb/guidelines.json")))
  File.open("wsg.md", "w") do |file|
    file.puts <<~EOD
      ---
      title: Sustainability Self-Assessment #{Date.today}
      layout: page
      ---
      Assessed against the #{json["title"]} version #{json["version"]} (#{json["edition"]}) on #{Date.today}.

    EOD
    json["category"].each do |category|
      next unless ["2", "3", "4"].include?(category["id"])
      if category["guidelines"]
        file.puts <<~EOD
          ## #{category["id"]}. #{category["name"]}

        EOD
        category["guidelines"].each do |guideline|
          file.puts <<~EOD
            ### #{category["id"]}.#{guideline["id"]}. [#{guideline["guideline"]}](#{guideline["url"]})

            #{guideline["description"]}

          EOD
          guideline["criteria"].each do |criterion|
            file.puts <<~EOD
              #### #{criterion["title"]}

              #{criterion["description"]}

              {:.not-assessed}
              Write assessment detail here.
              Change paragraph class to "bad", "ok", or "good" to set the evaluation overall result.

            EOD
          end
        end
      end
    end
  end
end
