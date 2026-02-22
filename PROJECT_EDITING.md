# Project Management Guide

This guide explains how to easily add, edit, and delete projects in your portfolio.

## Quick Start: Where to Edit Projects

**Edit this file:** [`src/constants/projects.js`](src/constants/projects.js)

That's it! You don't need to touch the complex nested structures or constants file anymore.

---

## How to Add a New Project

1. Open [`src/constants/projects.js`](src/constants/projects.js)
2. Add a new object to the `PROJECTS` array at the bottom:

```javascript
{
  name: "My Awesome Project",
  description: "One-line description shown in list",
  fullDescription: [
    "Line 1 of detailed description",
    "Line 2 of detailed description",
    // ... more lines
  ],
  icon: "/images/folder.png",
  position: "top-10 left-20",        // Desktop position (Tailwind classes)
  windowPosition: "top-[10vh] left-15", // Finder window position
  files: [
    {
      name: "My Project",
      type: "txt",
      description: ["Project description..."],
    },
    {
      name: "Visit Site",
      type: "url",
      href: "https://example.com",
    },
    {
      name: "Screenshot",
      type: "img",
      imageUrl: "/images/screenshot.png",
    },
    {
      name: "GitHub",
      type: "github",
      href: "https://github.com/username/repo",
    },
  ],
},
```

3. Save the file - **that's all!** The system automatically converts this to the internal format needed by your app.

---

## How to Edit a Project

Simply modify the project object in [`src/constants/projects.js`](src/constants/projects.js):

- **name**: Project folder name
- **description**: Short summary
- **fullDescription**: Array of paragraphs for the detailed view
- **position**: Where the folder icon appears on desktop (use Tailwind classes like `top-10 left-20`)
- **windowPosition**: Where the Finder window opens (use Tailwind classes)
- **files**: Array of files/links in the project folder

---

## How to Delete a Project

Simply remove the entire project object from the `PROJECTS` array in [`src/constants/projects.js`](src/constants/projects.js).

---

## File Types

You can add 4 types of files to each project:

### 1. **Text File** (`type: "txt"`)
Displays a description.

```javascript
{
  name: "Project Details",
  type: "txt",
  description: [
    "First paragraph",
    "Second paragraph",
    // ...
  ],
}
```

### 2. **URL/Website** (`type: "url"`)
Links to a website or GitHub repo.

```javascript
{
  name: "Visit Website",
  type: "url",
  href: "https://example.com",
}
```

### 3. **Image** (`type: "img"`)
Displays a screenshot or image.

```javascript
{
  name: "Screenshot",
  type: "img",
  imageUrl: "/images/my-project.png",
}
```

### 4. **GitHub** (`type: "github"`)
Link to GitHub repository.

```javascript
{
  name: "GitHub Repo",
  type: "github",
  href: "https://github.com/username/repo",
}
```

---

## Position Classes (Desktop Layout)

Use Tailwind classes for positioning:

- **Vertical**: `top-5`, `top-10`, `top-20`, `top-45`, `top-60`, `top-80` 
- **Horizontal**: `left-0`, `left-15`, `left-20`, `left-30`, `left-50`, `left-80` / `right-5`, `right-10`, `right-20`, `right-30`, `right-55`, `right-70`, `right-80`, `right-85`

Examples:
- `"top-10 left-20"` - Top-left area
- `"top-45 right-80"` - Top-right area  
- `"top-80 right-5"` - Bottom-right area

---

## Full Example: Adding a New Project

**Before:** Edit nested structure (confusing!)

```javascript
// Old way - lots of boilerplate
const WORK_LOCATION = {
  id: 1,
  type: "work",
  name: "Projects",
  // ... 300+ lines of nested objects ...
  children: [
    {
      id: 5,
      name: "Cyberpunk",
      // ... more nesting ...
    }
  ]
}
```

**After:** Clean, simple format (easy!)

```javascript
// New way - simple and clean
export const PROJECTS = [
  {
    name: "My Project",
    description: "What it does",
    fullDescription: ["Details..."],
    icon: "/images/folder.png",
    position: "top-10 left-20",
    windowPosition: "top-[10vh] left-15",
    files: [
      { name: "Description", type: "txt", description: ["..."] },
      { name: "Website", type: "url", href: "https://..." },
    ],
  },
  // ... more projects ...
];
```

---

## How It Works Behind the Scenes

The system uses:

1. **[`src/constants/projects.js`](src/constants/projects.js)** - Your clean project definitions
2. **[`src/constants/projectHelpers.js`](src/constants/projectHelpers.js)** - Utility functions that convert projects to the internal format
3. **[`src/constants/index.js`](src/constants/index.js)** - Main constants file that uses the helper to build the folder structure

You only edit `projects.js`! The rest is automatic.

---

## Utility Functions (Advanced)

If you need to programmatically access your projects, [`src/constants/projectHelpers.js`](src/constants/projectHelpers.js) provides:

```javascript
// Import utilities
import {
  buildWorkLocation,      // Generates the full work location
  findProject,            // Find project by name
  findFile,              // Find file in a project
  getProjectCount,       // Get number of projects
  getProjectNames,       // Get all project names
  getFileIcon,          // Get icon for file type
} from '#constants/projectHelpers';

// Examples:
const projectCount = getProjectCount();
const cyberpunk = findProject("Cyberpunk");
const website = findFile("Cyberpunk", "CyberpunkEdgerunners");
```

---

## Troubleshooting

### Build errors after editing?
- Check for missing commas in the `PROJECTS` array
- Make sure all strings are properly quoted
- Ensure file `type` is one of: `txt`, `url`, `img`, `github`

### Changes not showing?
- Save the file
- Restart the dev server (`npm run dev`)
- Clear browser cache if needed

### File icons not appearing?
- Verify the file `type` is correct
- Check that required fields are present (e.g., `description` for txt, `href` for url)

---

## That's it! 🎉

No more wrestling with nested structures. Just edit `projects.js` and go!
