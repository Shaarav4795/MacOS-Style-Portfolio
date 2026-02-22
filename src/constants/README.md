/**
 * QUICK START: How to Manage Projects
 * 
 * This directory contains the tools to make project management simple.
 * 
 * FILES:
 * 1. projects.js - EDIT THIS to add/modify/delete projects
 * 2. projectHelpers.js - Automatic converters (don't edit)
 * 3. index.js - Main constants (imports from projectHelpers)
 * 
 * WORKFLOW:
 * 
 * ADD PROJECT:
 *   Open projects.js → Add object to PROJECTS array → Save
 * 
 * EDIT PROJECT:
 *   Open projects.js → Modify the project object → Save
 * 
 * DELETE PROJECT:
 *   Open projects.js → Remove the project object → Save
 * 
 * FILES IN A PROJECT:
 *   - type: "txt"    → Description (has 'description' array)
 *   - type: "url"    → Link to website (has 'href')
 *   - type: "img"    → Image/screenshot (has 'imageUrl')
 *   - type: "github" → GitHub link (has 'href')
 * 
 * THAT'S IT!
 * No more editing nested structures. Simple and straightforward.
 * 
 * SEE: ../../PROJECT_EDITING.md for full documentation
 */

export { PROJECTS } from './projects';
export {
  buildWorkLocation,
  findProject,
  findFile,
  getProjectCount,
  getProjectNames,
  getFileIcon,
} from './projectHelpers';
