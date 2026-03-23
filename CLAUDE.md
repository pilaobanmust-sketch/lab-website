# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a Jekyll-based lab website template built on GitHub Pages. The site uses Manubot for automatic citation generation from simple identifiers (DOI, PubMed, ORCID) and includes automated workflows for content updates.

## Development Commands

### Local Development
```bash
# Install Ruby dependencies
bundle install

# Serve site locally (default: http://localhost:4000)
bundle exec jekyll serve
```

### Citation Management
```bash
# Install Python dependencies for citation processing
python -m pip install --upgrade --requirement ./_cite/requirements.txt

# Generate/update citations from data sources
python _cite/cite.py
```

The citation system processes files from `_data/` (sources.yaml, orcid.yaml, google-scholar.yaml, pubmed.yaml) and generates `_data/citations.yaml`.

### HTML Validation
```bash
# Run HTML proofer (controlled by proofer: true/false in _config.yaml)
bundle exec jekyll build
```

## Architecture

### Citation System
The citation pipeline is the core automation feature:

1. **Data Sources** (`_data/` directory):
   - `sources.yaml`: Manual citation entries with DOIs
   - `orcid.yaml`: ORCID IDs for automatic publication import
   - `google-scholar.yaml`: Google Scholar profiles (requires GOOGLE_SCHOLAR_API_KEY secret)
   - `pubmed.yaml`: PubMed queries

2. **Citation Processing** (`_cite/` directory):
   - `cite.py`: Main orchestrator that runs plugins sequentially
   - `plugins/`: Python modules for each data source type (google-scholar.py, orcid.py, pubmed.py, sources.py)
   - `util.py`: Shared utilities for Manubot integration and data handling
   - `.cache/`: Cached citation data to reduce API calls

3. **Workflow**:
   - Plugins expand data sources into individual sources
   - Sources with matching IDs are merged
   - Manubot generates full citations from identifiers
   - Output saved to `_data/citations.yaml`

### Jekyll Site Structure

- **Collections**:
  - `_members/`: Team member profiles (front matter: name, image, role, affiliation, links)
  - `_posts/`: Blog posts (front matter: title, image, author, tags)

- **Layouts** (`_layouts/`):
  - `default.html`: Base template
  - `member.html`: Individual team member pages
  - `post.html`: Blog post pages

- **Includes** (`_includes/`): Reusable components
  - `citation.html`: Renders citations with thumbnails and metadata
  - `card.html`, `button.html`, `feature.html`: UI components
  - `list.html`: Data listing with filtering
  - `portrait.html`: Team member portraits

- **Custom Plugins** (`_plugins/`): Ruby filters
  - `misc.rb`: Data filtering, variable handling, Google Fonts URL generation
  - `array.rb`, `hash.rb`, `file.rb`, `regex.rb`: Utility filters

- **Frontend** (`_scripts/`, `_styles/`):
  - Client-side search functionality
  - Dark mode toggle
  - Tag filtering
  - Anchor link handling

### GitHub Actions Workflows

- `build-site.yaml`: Builds and deploys to GitHub Pages
- `update-citations.yaml`: Runs citation pipeline, commits changes or opens PR
- `on-push.yaml`: Triggers build on main branch push
- `on-pull-request.yaml`: Builds preview deployments
- `on-schedule.yaml`: Periodic citation updates
- `first-time-setup.yaml`: One-time repo initialization

## Key Configuration

### _config.yaml
Main site configuration including:
- Site metadata (title, subtitle, description)
- Social media links (email, ORCID, GitHub, Twitter, YouTube)
- Jekyll collections and defaults
- Plugin configuration

### Content Management

**Adding citations**: Add entries to `_data/sources.yaml` with DOIs:
```yaml
- id: doi:10.1371/journal.pcbi.1007128
  type: paper
  description: Optional description with _markdown_
  image: optional-image-url
  buttons:
    - type: source
      link: https://github.com/repo
  tags:
    - tag1
    - tag2
```

**Adding team members**: Create markdown files in `_members/`:
```yaml
---
name: Full Name
image: images/photo.jpg
role: principal-investigator
affiliation: Institution
links:
  orcid: 0000-0001-2345-6789
---
Bio content here.
```

**Adding blog posts**: Create markdown files in `_posts/` with format `YYYY-MM-DD-title.md`:
```yaml
---
title: Post Title
image: images/photo.jpg
author: member-filename
tags: tag1, tag2
---
Post content here.
```

**Adding projects**: Edit `_data/projects.yaml`:
```yaml
- title: Project Name
  subtitle: Optional subtitle
  group: featured
  image: images/photo.jpg
  link: https://project-url.com
  description: Description with _markdown_
  repo: github-user/repo-name
  tags:
    - resource
```

## Environment Variables

- `GOOGLE_SCHOLAR_API_KEY`: Required for Google Scholar citation import (set in GitHub repository secrets)
- `JEKYLL_ENV`: Set to "production" for production builds

## Important Notes

- The citation cache (`./_cite/.cache/`) speeds up repeated builds by caching Manubot results
- Citations are automatically updated via scheduled workflows, but can be manually triggered
- Pull request previews are automatically built and deployed to a subfolder
- The `proofer` setting in `_config.yaml` controls HTML validation (disabled by default for faster builds)
- Front matter defaults are set in `_config.yaml` to automatically apply layouts to collections
