# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a LaTeX resume repository based on the Awesome CV template. The project compiles a professional resume/CV using XeLaTeX with modular content sections.

## Build System

### Build Commands
- `make` - Compiles the resume to PDF using XeLaTeX
- `make clean` - Removes generated PDF files
- `xelatex -output-directory=src src/resume.tex` - Direct compilation command

### Build Requirements
- XeLaTeX (part of TeX Live distribution)
- Uses `awesome-cv.cls` document class
- Docker alternative: `docker run --rm --user $(id -u):$(id -g) -i -w "/doc" -v "$PWD":/doc thomasweise/texlive make`

## Repository Structure

### Source Files
- `src/resume.tex` - Main LaTeX document with personal information and document structure
- `src/awesome-cv.cls` - LaTeX document class providing styling and commands
- `src/resume/` - Modular content sections:
  - `summary.tex` - Professional summary
  - `experience.tex` - Work experience
  - `education.tex` - Educational background
  - `honors.tex` - Awards and honors
  - `certificates.tex` - Certifications
  - `presentation.tex` - Presentations (commented out)
  - `writing.tex` - Publications (commented out)
  - `committees.tex` - Committee work (commented out)
  - `extracurricular.tex` - Activities (commented out)

### Configuration
- `Makefile` - Build automation
- `.yamllint.yaml` - YAML linting configuration for CI/CD files
- `.github/workflows/main.yml` - GitHub Actions workflow for PDF compilation

## Development Workflow

### Making Changes
1. Edit personal information in `src/resume.tex` (lines 54-78)
2. Modify content in individual section files under `src/resume/`
3. Run `make` to compile and generate `src/resume.pdf`
4. Review the generated PDF

### Customization
- Color scheme: Change `awesome-red` to other predefined colors (line 29 in `src/resume.tex`)
- Page layout: Modify geometry settings (line 24)
- Sections: Comment/uncomment `\input{}` statements (lines 100-108) to include/exclude sections
- Styling: Modify `src/awesome-cv.cls` for deeper customization

### CI/CD
- GitHub Actions automatically compiles PDFs on push/PR using TeX Live container
- Artifacts are uploaded for download

## LaTeX-Specific Notes
- Uses XeLaTeX engine for better font support
- Encoding: UTF-8 Unicode
- Paper size: A4 (can be changed to letterpaper)
- Font requirements: Roboto and Source Sans Pro (handled by document class)