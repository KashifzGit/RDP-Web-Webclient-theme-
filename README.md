RD Web Access and Web Client Theme Development Tutorial
Show Image
Show Image
Show Image
A comprehensive guide to developing custom themes for Remote Desktop Web Access (RD Web Access) and RDS Web Client. Learn to customize the appearance and branding of your RD Web interface.
Table of Contents

Overview
Prerequisites
Architecture
Getting Started
Customizing Login Page
Customizing Connection Center
Adding Assets
Responsive Design
Deployment
Advanced Features
Testing
Best Practices
Troubleshooting
Contributing
License


Overview
Remote Desktop (RD) Web Access provides a browser-based interface for accessing remote desktops and applications. Theme development allows you to customize the appearance and branding of the RD Web client to match your organization's identity and requirements.
This tutorial covers:

Creating custom themes from scratch
Styling the login/logon page
Customizing the connection center interface
Integrating custom images and assets
Implementing responsive design
Deploying themes to production
Advanced customization techniques


Prerequisites
Before starting, ensure you have:

Windows Server 2012 R2 or later with Remote Desktop Services installed
Remote Desktop Web Access role service enabled
Basic knowledge of HTML, CSS, and JavaScript
Administrator access to the RDS server
Text editor or IDE for development (Visual Studio Code, Sublime Text, etc.)
Modern web browser for testing (Edge, Chrome, Firefox, Safari)


Architecture
Key Components
ComponentDescriptionLocationRDClientHost.htmlMain entry point for web clientWeb rootThemes FolderTheme storage directory%ProgramFiles%\\Rds\\Web\\App_ThemesCSS FilesStyle sheets for themingTheme folderJavaScript FilesClient-side logicTheme folderImage AssetsLogo, backgrounds, iconsApp_Themes\\YourTheme\\images
Directory Structure
%ProgramFiles%\\Remote Desktop Services\\Web Access\\App_Themes\\
├── Default/
│   ├── theme.css
│   ├── logon.css
│   ├── theme-rtl.css
│   └── images/
│       ├── logo.png
│       ├── background.jpg
│       └── icons/
├── CustomTheme/
│   ├── theme.css
│   ├── logon.css
│   ├── theme-rtl.css
│   └── images/

Getting Started
Step 1: Create Theme Directory
bash# Navigate to themes folder
cd "%ProgramFiles%\\Remote Desktop Services\\Web Access\\App_Themes"

# Create new theme directory
mkdir MyCustomTheme
cd MyCustomTheme

# Create subdirectories
mkdir images
Step 2: Copy Base Files
Copy the following files from the Default theme:

theme.css - Main stylesheet for connection center
logon.css - Login page stylesheet
theme-rtl.css - Right-to-left language support

bash# Copy from Default theme (adjust path as needed)
copy ..\\Default\\theme.css .
copy ..\\Default\\logon.css .
copy ..\\Default\\theme-rtl.css .
Step 3: Create Folder Structure
Ensure your theme has this structure:
MyCustomTheme/
├── theme.css
├── logon.css
├── theme-rtl.css
├── theme.js (optional)
└── images/
    ├── logo.png
    ├── background.jpg
    └── icons/

Customizing Login Page
logon.css Examples
Brand Logo
css/* Logo and branding */
.brandinglogo {
    background-image: url('images/mylogo.png');
    background-size: contain;
    background-repeat: no-repeat;
    width: 300px;
    height: 100px;
    margin: 0 auto;
}
Background Styling
css/* Login page background */
body.logon {
    background-color: #f0f0f0;
    background-image: 
        linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.3)),
        url('images/background.jpg');
    background-size: cover;
    background-position: center;
    background-attachment: fixed;
}
Form Container
css/* Login form container */
.formcontainer {
    background-color: #ffffff;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    padding: 30px;
    max-width: 400px;
    margin: 0 auto;
}

/* Form title */
.formtitle {
    font-size: 20px;
    font-weight: 600;
    color: #333333;
    margin-bottom: 20px;
    text-align: center;
}
Input Fields
css/* Text and password inputs */
input[type="text"],
input[type="password"] {
    width: 100%;
    border: 1px solid #cccccc;
    padding: 10px 12px;
    margin: 8px 0;
    border-radius: 4px;
    font-size: 14px;
    box-sizing: border-box;
    transition: border-color 0.3s ease;
}

input[type="text"]:focus,
input[type="password"]:focus {
    outline: none;
    border-color: #0078d4;
    box-shadow: 0 0 5px rgba(0, 120, 212, 0.3);
}
Buttons
css/* Login button */
.button,
input[type="button"] {
    width: 100%;
    background-color: #0078d4;
    color: white;
    border: none;
    padding: 10px 20px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
    font-size: 14px;
    transition: background-color 0.3s ease;
    margin-top: 15px;
}

.button:hover,
input[type="button"]:hover {
    background-color: #005a9e;
}

.button:active,
input[type="button"]:active {
    background-color: #003d7a;
}
Error Messages
css/* Error messages */
.errormessage,
.error {
    background-color: #ffebee;
    color: #d32f2f;
    border-left: 4px solid #d32f2f;
    padding: 12px;
    margin: 15px 0;
    border-radius: 2px;
    font-weight: 500;
}

/* Warning messages */
.warning {
    background-color: #fff3e0;
    color: #e65100;
    border-left: 4px solid #e65100;
    padding: 12px;
    margin: 15px 0;
}
Checkboxes and Links
css/* Checkbox styling */
input[type="checkbox"] {
    margin-right: 8px;
    cursor: pointer;
}

/* Links */
a {
    color: #0078d4;
    text-decoration: none;
    transition: color 0.3s ease;
}

a:hover {
    color: #005a9e;
    text-decoration: underline;
}

Customizing Connection Center
theme.css Examples
Overall Layout
css/* Page styling */
html, body {
    margin: 0;
    padding: 0;
    background-color: #f5f5f5;
    font-family: 'Segoe UI', -apple-system, BlinkMacSystemFont, sans-serif;
    color: #333333;
    height: 100%;
}

* {
    box-sizing: border-box;
}
Header Bar
css/* Header/Navigation bar */
#header,
.header {
    background-color: #0078d4;
    color: white;
    padding: 15px 20px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    display: flex;
    align-items: center;
    justify-content: space-between;
}

/* Header logo */
.headerlogo {
    background-image: url('images/logo-white.png');
    background-size: contain;
    background-repeat: no-repeat;
    width: 40px;
    height: 40px;
    display: inline-block;
}

/* Header title */
.headertitle {
    font-size: 18px;
    font-weight: 600;
    margin-left: 15px;
    display: inline-block;
}
Workspace Tiles
css/* Desktop/Application tiles container */
.workspaces,
.workspace-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 15px;
    padding: 20px;
}

/* Individual workspace item */
.workspaceitem,
.workspace-tile {
    background-color: white;
    border: 1px solid #e0e0e0;
    border-radius: 6px;
    padding: 15px;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05);
}

.workspaceitem:hover,
.workspace-tile:hover {
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
    transform: translateY(-2px);
    border-color: #0078d4;
}

/* Workspace icon */
.workspace-icon {
    width: 48px;
    height: 48px;
    margin-bottom: 10px;
}

/* Workspace title */
.workspacetitle,
.workspace-name {
    font-size: 16px;
    font-weight: 600;
    color: #000000;
    margin: 10px 0 5px 0;
}

/* Workspace description */
.workspacedescription,
.workspace-description {
    font-size: 13px;
    color: #666666;
    line-height: 1.4;
}
Navigation Menu
css/* Side navigation menu */
.navmenu,
.sidebar {
    background-color: #f9f9f9;
    border-right: 1px solid #e0e0e0;
    padding: 0;
    width: 220px;
}

/* Menu items */
.navmenuitem,
.menu-item {
    padding: 12px 20px;
    color: #333333;
    cursor: pointer;
    border-left: 3px solid transparent;
    transition: all 0.3s ease;
}

.navmenuitem:hover,
.menu-item:hover {
    background-color: #e8e8e8;
}

/* Active menu item */
.navmenuitem.active,
.menu-item.active {
    background-color: #e3f2fd;
    border-left-color: #0078d4;
    color: #0078d4;
    font-weight: 600;
}
Buttons
css/* Primary button */
.primarybutton,
.btn-primary {
    background-color: #0078d4;
    color: white;
    border: none;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: 500;
    transition: background-color 0.3s ease;
}

.primarybutton:hover,
.btn-primary:hover {
    background-color: #005a9e;
}

/* Secondary button */
.secondarybutton,
.btn-secondary {
    background-color: #ffffff;
    color: #0078d4;
    border: 1px solid #0078d4;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: 500;
    transition: all 0.3s ease;
}

.secondarybutton:hover,
.btn-secondary:hover {
    background-color: #f0f8ff;
}

/* Danger button */
.dangerbutton,
.btn-danger {
    background-color: #d32f2f;
    color: white;
    border: none;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
}

.dangerbutton:hover,
.btn-danger:hover {
    background-color: #b71c1c;
}
Dialogs and Modals
css/* Modal/Dialog overlay */
.modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;
}

/* Modal dialog */
.modal {
    background-color: white;
    border-radius: 8px;
    box-shadow: 0 5px 40px rgba(0, 0, 0, 0.3);
    max-width: 500px;
    width: 90%;
    padding: 20px;
}

/* Modal header */
.modal-header {
    border-bottom: 1px solid #e0e0e0;
    padding-bottom: 15px;
    margin-bottom: 15px;
}

/* Modal title */
.modal-title {
    font-size: 18px;
    font-weight: 600;
    color: #333333;
}

/* Modal content */
.modal-content {
    padding: 15px 0;
}

/* Modal footer */
.modal-footer {
    border-top: 1px solid #e0e0e0;
    padding-top: 15px;
    margin-top: 15px;
    text-align: right;
}

.modal-footer .button {
    margin-left: 10px;
}

Adding Assets
Image Specifications
Asset TypeFormatSizeOptimizationLogoPNG300x100px<100KBBackgroundJPG1920x1200px<500KBIconsPNG32x32 or 48x48px<50KB eachFaviconICO16x16px<10KB
Image Integration
css/* Logo on login page */
.brandinglogo {
    background-image: url('images/company-logo.png');
    background-size: contain;
    background-repeat: no-repeat;
}

/* Background with overlay gradient */
body.logon {
    background-image: 
        linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.3)),
        url('images/background.jpg');
    background-size: cover;
    background-position: center;
}

/* Desktop icon */
.icon-desktop {
    background-image: url('images/icon-desktop.png');
    width: 48px;
    height: 48px;
}

/* Application icon */
.icon-app {
    background-image: url('images/icon-app.png');
    width: 32px;
    height: 32px;
}
Creating images
Logo Creation

Use transparent PNG format
Ensure text is readable on colored backgrounds
Test at different zoom levels
Keep file size minimal

Background Image

Use JPG format for compression
Choose subtle patterns or photography
Ensure good contrast for overlaid text
Optimize dimensions for web


Responsive Design
Mobile-Friendly Theme
css/* Extra small devices (phones) */
@media (max-width: 480px) {
    body {
        font-size: 14px;
    }
    
    .formcontainer {
        max-width: 95%;
        padding: 15px;
    }
    
    input[type="text"],
    input[type="password"] {
        font-size: 16px; /* Prevents zoom on iOS */
    }
    
    .workspaceitem {
        width: 100%;
        margin: 10px 0;
    }
}

/* Small devices (tablets in portrait) */
@media (max-width: 768px) {
    #header {
        padding: 10px 15px;
    }
    
    .headertitle {
        font-size: 16px;
    }
    
    .navmenu {
        display: none;
    }
    
    .workspaces {
        grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
        gap: 10px;
        padding: 10px;
    }
    
    .workspaceitem {
        padding: 10px;
    }
}

/* Medium devices (tablets in landscape) */
@media (max-width: 1024px) {
    .workspaces {
        grid-template-columns: repeat(2, 1fr);
        gap: 15px;
    }
}

/* Large devices (desktops) */
@media (min-width: 1025px) {
    .workspaces {
        grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
        gap: 20px;
    }
}
Responsive Typography
css/* Responsive font sizing */
body {
    font-size: 16px;
}

h1 { font-size: 28px; }
h2 { font-size: 24px; }
h3 { font-size: 20px; }

@media (max-width: 768px) {
    body { font-size: 14px; }
    h1 { font-size: 22px; }
    h2 { font-size: 18px; }
    h3 { font-size: 16px; }
}

@media (max-width: 480px) {
    body { font-size: 13px; }
    h1 { font-size: 20px; }
    h2 { font-size: 16px; }
    h3 { font-size: 14px; }
}

Deployment
Windows Server 2012 R2 - 2019
Step 1: Prepare Theme Files
bash# Ensure all files are in the correct location
%ProgramFiles%\\Rds\\Web\\App_Themes\\YourThemeName\\
├── theme.css
├── logon.css
├── theme-rtl.css
└── images/
Step 2: Configure IIS

Open Internet Information Services (IIS) Manager
Navigate to Remote Desktop Web Access application
Right-click and select Explore to verify theme files

Step 3: Update Configuration (if needed)
Edit %ProgramFiles%\\Rds\\Web\\web.config:
xml<configuration>
  <appSettings>
    <add key="ThemeName" value="YourThemeName" />
  </appSettings>
</configuration>
Step 4: Restart Services
bashiisreset /restart
Step 5: Clear Cache
Users should clear browser cache:

Edge/Chrome: Ctrl + Shift + Delete
Firefox: Ctrl + Shift + Delete
Safari: Cmd + Shift + Delete

Windows Server 2022 with Windows 11

Deploy theme to same directory structure
Configuration may be handled through Group Policy or PowerShell
Access https://servername/rdweb to verify


Advanced Features
Custom JavaScript (theme.js)
javascript// Custom theme initialization
(function() {
    'use strict';
    
    document.addEventListener('DOMContentLoaded', function() {
        console.log('Custom theme initializing...');
        
        // Initialize branding
        initializeBranding();
        
        // Setup event listeners
        setupEventListeners();
        
        // Apply custom behaviors
        applyCustomBehaviors();
        
        console.log('Custom theme loaded successfully');
    });
    
    function initializeBranding() {
        var header = document.getElementById('header');
        if (header) {
            header.setAttribute('data-company', 'MyCompany');
            console.log('Branding initialized');
        }
    }
    
    function setupEventListeners() {
        var workspaceItems = document.querySelectorAll('.workspaceitem');
        
        workspaceItems.forEach(function(item) {
            item.addEventListener('mouseenter', function() {
                this.classList.add('active');
            });
            
            item.addEventListener('mouseleave', function() {
                this.classList.remove('active');
            });
        });
    }
    
    function applyCustomBehaviors() {
        // Add custom behaviors here
        var buttons = document.querySelectorAll('.primarybutton');
        buttons.forEach(function(btn) {
            btn.addEventListener('click', function(e) {
                console.log('Button clicked:', this.textContent);
            });
        });
    }
})();
CSS Custom Properties (Variables)
css/* Define color scheme as CSS variables */
:root {
    --primary-color: #0078d4;
    --primary-dark: #005a9e;
    --primary-light: #e3f2fd;
    --background-color: #f5f5f5;
    --surface-color: #ffffff;
    --text-color: #333333;
    --text-secondary: #666666;
    --border-color: #e0e0e0;
    --border-radius: 6px;
    --shadow-small: 0 1px 3px rgba(0, 0, 0, 0.05);
    --shadow-medium: 0 4px 12px rgba(0, 0, 0, 0.15);
}

/* Use variables throughout theme */
.primarybutton {
    background-color: var(--primary-color);
    color: white;
    border-radius: var(--border-radius);
}

.primarybutton:hover {
    background-color: var(--primary-dark);
}

body {
    background-color: var(--background-color);
    color: var(--text-color);
}

.workspaceitem {
    background-color: var(--surface-color);
    border-color: var(--border-color);
    box-shadow: var(--shadow-small);
}
Dark Mode Support
css/* Dark mode support */
@media (prefers-color-scheme: dark) {
    :root {
        --primary-color: #0078d4;
        --background-color: #1e1e1e;
        --surface-color: #2d2d2d;
        --text-color: #ffffff;
        --text-secondary: #b0b0b0;
        --border-color: #404040;
    }
    
    body {
        background-color: var(--background-color);
        color: var(--text-color);
    }
    
    .workspaceitem {
        background-color: var(--surface-color);
    }
}

Testing
Testing Checklist

 Logo displays correctly on both login and connection center
 Colors match brand guidelines
 All buttons are clickable and properly styled
 Forms are properly aligned and functional
 Mobile layout is responsive on tablets
 Mobile layout is responsive on smartphones
 No broken image links
 No console errors in browser DevTools
 Login page displays correctly
 Connection center displays workspaces
 Hover effects work as intended
 Page loads quickly (<2 seconds)
 Accessibility: color contrast is sufficient
 Tested in multiple browsers

Testing on Multiple Browsers
✓ Microsoft Edge (latest)
✓ Google Chrome (latest)
✓ Mozilla Firefox (latest)
✓ Apple Safari (latest)
✓ Mobile Safari (iOS)
✓ Chrome Mobile (Android)
Browser DevTools Inspection
javascript// Open console (F12) and check for errors
// Check applied CSS: Right-click > Inspect
// Mobile simulation: Ctrl+Shift+M
// Performance: Ctrl+Shift+I > Performance tab

Best Practices
Performance

✅ Optimize images aggressively using tools like TinyPNG
✅ Minimize CSS and remove unused styles
✅ Use CSS variables for maintainability
✅ Avoid inline styles and scripts
✅ Lazy load images when appropriate
✅ Minimize HTTP requests
✅ Use modern image formats (WebP with fallback)

Accessibility

✅ Maintain WCAG AA color contrast minimum (4.5:1 for text)
✅ Include alt text for images
✅ Ensure keyboard navigation works
✅ Use semantic HTML
✅ Avoid color-only indicators
✅ Test with screen readers

Security

✅ Validate and sanitize all user inputs
✅ Use HTTPS for all connections
✅ Avoid inline scripts
✅ Use Content Security Policy headers
✅ Keep dependencies updated
✅ Don't embed sensitive information in CSS/JS

Maintenance

✅ Document all customizations
✅ Keep backups of original theme
✅ Version control your themes
✅ Test before deploying to production
✅ Create a development/staging environment
✅ Maintain changelog


Troubleshooting
Theme Not Appearing
Problem: Custom theme is not showing up
Solutions:
bash# Clear IIS cache
iisreset /restart

# Clear browser cache (Ctrl + Shift + Delete)

# Verify theme folder name matches configuration
# Check that all CSS files are present
# Restart RDS services
Images Not Loading
Problem: Images are broken or missing
Solutions:

Verify image file paths are relative: url('images/logo.png')
Check image file permissions (IIS must have read access)
Verify image files exist in the correct folder
Check file names are case-sensitive on Linux servers
Use browser DevTools (F12) to see exact error

Styling Not Applied
Problem: CSS changes aren't appearing
Solutions:
bash# Hard refresh browser: Ctrl + F5
# Clear browser cache completely
# Check CSS syntax is valid (use CSS validator)
# Check for higher specificity CSS rules overriding your styles
# Verify IIS has permissions to read theme folder
Login Page Issues
Problem: Login page not styled correctly
Solutions:

Verify logon.css exists in theme folder
Check image paths in CSS are correct
Ensure IIS has read permissions on theme files
Test in private/incognito window
Check browser console for errors (F12)

Performance Issues
Problem: Page loads slowly
Solutions:
bash# Reduce image file sizes
# Minimize CSS and JavaScript
# Use image optimization tools
# Check for unoptimized background images
# Profile with browser DevTools (F12 > Performance)
CSS Specificity Issues
Problem: Your CSS rules are being overridden
Solutions:
css/* Use more specific selectors */
#main .workspaceitem { /* more specific */ }

/* Use !important only as last resort */
.button { color: blue !important; }

/* Avoid conflicting class names */
Right-to-Left (RTL) Languages
Problem: RTL languages not displaying correctly
Solution: Maintain theme-rtl.css with RTL-specific styles
css/* theme-rtl.css */
body[dir="rtl"] {
    direction: rtl;
    text-align: right;
}

body[dir="rtl"] .workspaceitem {
    margin-left: 0;
    margin-right: 10px;
}

FAQ
Q: Can I use a custom theme with multiple RDS servers?
A: Yes, copy your theme to each server's App_Themes folder.
Q: How do I revert to the default theme?
A: Remove or rename your custom theme folder, restart IIS.
Q: Can I use JavaScript in my theme?
A: Yes, but keep it minimal for security and performance. Store in theme.js.
Q: Is my custom theme preserved after RDS updates?
A: Usually yes, but always backup your theme before applying updates.
Q: Can I customize the RDS client (not just web)?
A: This tutorial focuses on RD Web Access. Native client customization differs.

Contributing
Contributions are welcome! Please:

Test your changes thoroughly
Document any new features
Ensure accessibility compliance
Optimize images
Submit pull request with clear description


License
This tutorial is provided as-is for educational purposes. Customize as needed for your organization.
MIT License - See LICENSE file for details.

Resources

Remote Desktop Services on Microsoft Docs
IIS Configuration Reference
WCAG 2.1 Accessibility Guidelines
CSS Tricks - A Complete Guide to Grid
MDN Web Docs - CSS Reference


Support
For issues or questions:

Check the Troubleshooting section
Review the FAQ
Check browser console (F12) for errors
Refer to Microsoft RDS documentation
Consult your system administrator


Last Updated: 2024
Maintainer: RD Web Theme Development Community

Quick Start Summary
bash# 1. Create theme directory
mkdir "%ProgramFiles%\\Rds\\Web\\App_Themes\\MyTheme"

# 2. Copy base files from Default theme
# 3. Customize theme.css and logon.css
# 4. Add images to images/ subfolder
# 5. Restart IIS
iisreset /restart

# 6. Test at https://yourserver/rdweb
# 7. Clear browser cache if changes don't appear

Made with ❤️ for Remote Desktop administrators and developers
