# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

- `python3 -m http.server 8000` - Start local development server at http://localhost:8000
- `git push origin main` - Push changes (auto-deploys to production via GitHub Actions)

## Project Architecture

This is a minimalistic personal website for Mike Rowan built as a static single-page site:

### Core Files Structure
- `index.html` - Single HTML file containing the entire website
- `styles.css` - CSS with responsive design, dark mode support, and custom properties
- `peru-photo.jpg` - Profile image from Peru hiking trip
- `vercel.json` - Vercel deployment configuration

### Design System
- **Minimalistic approach**: Clean, centered layout with plenty of white space
- **CSS Variables**: Theme system using custom properties for colors and spacing
- **Responsive**: Mobile-first design with breakpoints at 768px and 480px
- **Dark Mode**: Automatic dark mode support via `prefers-color-scheme`
- **Typography**: System fonts with careful font weight and spacing choices

### CI/CD Pipeline
Simple automated deployment via GitHub Actions:

#### Workflow
- **Direct commits to main** - No branch protection for simplicity
- Push to main triggers automatic deployment to Vercel
- Quick HTML validation check before deploy
- Production auto-deploys in ~30 seconds

#### Required GitHub Secrets
- `VERCEL_TOKEN` - Vercel CLI authentication token
- `VERCEL_ORG_ID` - team_xKGi93onow6tB8gPVuF1s4zK  
- `VERCEL_PROJECT_ID` - prj_LYKS9HG5pxuedYipr7CekX2u8ncM
- `VERCEL_SCOPE` - mikerowans-projects

#### Simplified Testing
- Basic HTML structure check on deploy
- Manual testing recommended before pushing to main

### Content Structure
- **Hero Section**: Profile photo, name "Mike Rowan", tagline "Builder. Operator. Advisor. Mentor."
- **About Section**: Professional background without heading (commented out for space)
- **Social Links**: LinkedIn and Instagram as SVG icons with hover effects
- **Footer**: Copyright notice

### Deployment
- **Production**: https://personal-website-mikerowans-projects.vercel.app
- **Local Development**: Served via Python's built-in HTTP server
- **Preview**: Automatic Vercel preview URLs for PRs

The site emphasizes simplicity and performance over complex functionality.