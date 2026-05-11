require "dotenv"
Dotenv.load

require "octokit"

task default: :download_release_notes

desc "Downloads latest release notes and creates news posts"
task :download_release_notes do
  client = Octokit::Client.new(access_token: ENV.fetch("GITHUB_ACCESS_TOKEN"))
  releases = client.releases("manyfold3d/manyfold")
  create_latest_release_file(releases.first)
  releases.each do |release|
    create_release_notes_file(release)
  end
end

def create_latest_release_file(release)
  File.open("_data/releases.yml", "w") do |f|
    f.puts <<~EOF
      ---
      latest:
        name: #{release.name}
        path: #{permalink(release)}
    EOF
  end
end

def create_release_notes_file(release)
  File.open("_posts/#{filename(release)}.md", "w") do |f|
    f.puts <<~EOF
      ---
      title: Release #{release.name}
      date: #{release.published_at}
      category: releases
      ---
      #{fix_links release.body}

      See the original release on GitHub: [#{release.name}](#{release.html_url})
    EOF
  end
end

def filename(release)
  [
    release.published_at.strftime("%F"),
    "release",
    release.name.tr(".", "-")
  ].join("-")
end

def permalink(release)
  [
    "",
    "news",
    release.published_at.strftime("%Y/%m/%d"),
    "release-#{release.name.tr(".", "-")}.html"
  ].join("/")
end

def fix_links(markdown)
  markdown.gsub!(/https:\/\/github.com\/([\w\/]+)\/pull\/([0-9]+)/, "[#\\2](https://github.com/\\1/pull/\\2)")
  markdown.gsub!(/(\s)@(\w+)(\s)/, "\\1[@\\2](https://github.com/\\2)\\3")
  markdown.gsub!(/https:\/\/github.com\/([\w\/]+)\/compare\/([\w.]+)/, "[\\2](https://github.com/\\1/compare/\\2)")
  markdown
end
