
# Enhanced MITRE ATT&CK® Coverage Tracker
> MITRE ATTACK Framework: Enterprise MITRE Matrix for SOC Teams

Welcome to the Enhanced MITRE ATT&CK® Coverage Tracker, designed for Security Operations Centers (SOCs) to manage and measure the coverage of MITRE ATT&CK® tactics and techniques. This project provides SOC analysts and security consultants with a simple, portable, and effective tool for gaining insights into their defensive capabilities against cyber threats.

> [!NOTE]
> Built on top of MITRE ATT&CK® framework as of ATT&CK v16.1, October 31, 2024 - April 21, 2025.

## 🌐 Web Application (NEW!)

**Access the live web application here:** [MITRE ATT&CK Coverage Tracker](https://quitehacker.github.io/MITRE-ATTACK-Enterprise-Matrix-in-Excel-for-SOC/)

The coverage tracker is now available as a fully web-based application that:
- **Automatically fetches** the latest MITRE ATT&CK data from their official GitHub repository
- **Works entirely in your browser** - no installation or backend required
- **Stores your data locally** using browser localStorage for privacy
- **Import/Export functionality** to backup and share your coverage data
- **Real-time updates** - see your coverage metrics update as you add detection rules
- **Mobile-friendly** responsive design for on-the-go access
- **Always up-to-date** with the latest MITRE ATT&CK framework

### Web Application Features
- **Dashboard**: Overview of your coverage metrics and statistics
- **Coverage Matrix**: Visual representation of detection coverage by tactic
- **Techniques View**: Searchable and filterable list of all techniques
- **Detection Rules**: Manage your detection rules with an intuitive interface
- **Data Sources**: Track which data sources are available in your environment

### Getting Started with the Web App
1. Visit the [web application](https://quitehacker.github.io/MITRE-ATTACK-Enterprise-Matrix-in-Excel-for-SOC/)
2. Start adding your detection rules in the "Detections" tab
3. Mark your available data sources in the "Data Sources" tab
4. Monitor your coverage in real-time on the Dashboard
5. Export your data anytime to backup or share with your team

## 📊 Excel Version

The original Excel-based tracker is still available for those who prefer offline analysis or need Excel-specific features.

## Screenshots
### Coverage
Provides a visual representation of detection coverage across the ATT&CK framework, highlighting well-covered areas and those requiring further attention. It's essential for quick assessments and strategic planning for coverage improvement.

![Coverage](images/Coverage.png)

### Techniques
Focused on the individual techniques outlined by MITRE ATT&CK®, this sheet allows for detailed mapping of detection rules against specific techniques and sub-techniques. Users can document their detection coverage, note available data sources, and identify areas lacking detection capability.

![Techniques](images/Techniques.png)

### Detections
The core of the workbook, where users input and manage their specific detection rules. This sheet enables mapping these rules to ATT&CK techniques and sub-techniques, facilitating a clear view of coverage and gaps in detection capabilities.

![Detections](images/Detections.png)

### Sources
Lists the data sources that can be leveraged to detect the techniques, allowing for a comprehensive check of whether the necessary data is being collected for effective detection and response.

![Detections](images/Sources.png)

### Progress
Overall progress or coverage of all the detection rules you have in place.
#### Basic Progress
![Detections](images/Basic_Progress.png)
#### Advanced Progress
![Detections](images/Advanced_Progress.png)

## Project Goal

This project provides two ways to assess the coverage of MITRE ATT&CK® tactics and techniques based on your detection rules:

1. **Web Application** (Recommended): A modern, browser-based tool that automatically fetches the latest MITRE data
2. **Excel Workbook**: The original `MITRE ATT&CK Enterprise Matrix for SOC.xlsx` for offline analysis

Both tools are crafted for DFIR consultants and SOC analysts working across various environments, offering a unique way to visualize readiness against attacker tactics and pinpoint areas needing improvement.

## Features of the Coverage Tracker

- **Comprehensive Worksheets**: The Excel workbook is divided into intuitive worksheets, each designed to facilitate different aspects of your analysis. From inputting detection rules to visualizing technique coverage, the worksheets serve as a guide through your ATT&CK® coverage journey.
- **User-Friendly Design**: With a mix of colored headers for ease of navigation - gray for static fields, blue for calculated values, and white for user inputs - the workbook is designed for straightforward use. Focus on white columns for inputs to mark detection rules as active or to map them to specific ATT&CK® techniques.
- **Detailed Guidance**: From adding your first detection rule to understanding the coverage of techniques and sub-techniques, the documentation guides you every step of the way. Visual indicators, such as red for inconsistencies and green for detected techniques, make it easy to assess your SOC's readiness at a glance.

# Excel Workbook Guide for MITRE ATT&CK® Coverage
Welcome to the comprehensive guide for utilizing the Excel workbook to track and enhance your security operations center's (SOC) coverage of the MITRE ATT&CK® framework. This document will walk you through each step, from adding your first detection rule to customizing the workbook to fit unique needs.

## Getting Started with Detection Rules
### Adding Your First Detection Rule
The journey to enhance your defensive capabilities starts in the Detections worksheet. This sheet is the heart of the workbook where you'll catalog your SOC's detection rules.

* The Worksheet Layout: The first four columns are provided as examples. You're encouraged to tailor these columns to suit your needs, except for the "is active" and "attack1..3" columns which are essential for the workbook's logic.
* Activating a Detection Rule: To activate a detection rule, simply input "yes" in the appropriate column. This action signifies that the rule is currently in use.
* Mapping to Techniques: Utilize the "attack1..3" columns to map your detection rule to specific ATT&CK techniques or sub-techniques, such as attempting to access LSASS Memory (sub-technique T1003.001).

### The Techniques Worksheet
After mapping your detection rule, switch to the Techniques worksheet to observe the impact. You might notice lines highlighted in red, indicating an inconsistency - a detection rule exists without the necessary data source for detection.

* Resolving Inconsistencies: To rectify this, verify the "data source available" column. If it reports zero, you'll need to ensure that the corresponding data source is marked as "yes" in the Sources worksheet.

## Enhancing Your Coverage
### Understanding Coverage and Status
The Status and Coverage worksheets provide a visual representation of your current detection capabilities:

* Status Worksheet: Offers a snapshot of what techniques and sub-techniques are currently detected by your rules, as well as those missing detection entirely.
* Coverage Worksheet: Provides a percentage-based overview of your detection rule coverage against the total techniques listed under each tactic.

## Customizing and Expanding Coverage
### Adding New Techniques
If you encounter a new sub-technique not included in the framework, you can add it directly to the detections worksheet and link it to the relevant technique.

### Adjusting for Direct Technique Detection
In cases where a technique with sub-techniques receives a direct detection rule, adjust the "detection rules modifier" column to account for this. This ensures your coverage calculation remains accurate.

### Disabling Irrelevant Techniques
Utilize the "detection rules modifier" in the techniques worksheet to disable any technique or sub-technique not relevant to your environment, such as those specific to operating systems you do not use.

### Managing Custom Data Sources
If your SOC utilizes data sources not listed in the ATT&CK framework, add these to the Sources worksheet and update the techniques accordingly to reflect these new sources.

## Technical Details

### Web Application Architecture
The web application is built with:
- **Frontend**: Pure HTML5, CSS3, and vanilla JavaScript (no dependencies)
- **Data Source**: MITRE ATT&CK data fetched from `https://raw.githubusercontent.com/mitre/cti/master/enterprise-attack/enterprise-attack.json`
- **Storage**: Browser localStorage for user data (detection rules and data sources)
- **Hosting**: GitHub Pages (static site hosting)

### Data Privacy
All your detection rules and data source configurations are stored locally in your browser. No data is sent to any server. You can export your data at any time for backup or sharing purposes.

### Browser Compatibility
The web application works on all modern browsers:
- Chrome/Edge (recommended)
- Firefox
- Safari
- Opera

### Contributing
Contributions are welcome! Feel free to:
- Report bugs or request features via GitHub Issues
- Submit pull requests for improvements
- Share your feedback and suggestions

## Future Updates

Stay tuned for updates including:
- Additional visualization options
- Coverage comparison over time
- Integration with SIEM platforms
- Custom technique/sub-technique support
- Export to various formats (PDF, CSV, etc.)

Your feedback and contributions are welcome to help evolve this tool.

## Credits

Special thanks to:
- Roberto Rodriguez (@Cyb3rWard0g) & RealityNet, which inspired this project
  - https://cyberwardog.blogspot.com/2017/07/how-hot-is-your-hunt-team.html
  - https://github.com/RealityNet/attack-coverage
- MITRE Corporation for maintaining the ATT&CK framework
  - https://github.com/mitre/cti
  - https://attack.mitre.org/

## License

This project is licensed under the terms specified in the LICENSE file.
