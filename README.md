# IT Concierge Agent (Copilot Studio)

An IT help desk agent I built in Microsoft Copilot Studio. It helps an employee troubleshoot a technical issue, or find and request a device, and it sends the finished request to IT by email.

Built while working through [Microsoft's Agent Academy](https://microsoft.github.io/agent-academy/recruit-nextgen/) (Recruit NextGen, Microsoft Copilot harness path). The lab gave me the scenario and starter skills. The changes below are mine. All data is sample data in my own Microsoft 365 developer tenant.

## The problem

Employees ask IT the same things over and over: "My email stopped coming in" and "I need a new laptop." Someone has to answer, check what is in stock, and write up the request.

## What the agent does

**1. Troubleshooting** (`skills/troubleshooting-procedure.md`)
Asks one focused question if it needs to, tries safe quick checks first, gives short numbered steps with source links, offers alternatives, and closes cleanly once the issue is fixed. After two or three failed paths it recommends escalating to IT with a ticket summary.

**2. Device requests** (`skills/device-guidance-v1-0-4.md`)
Looks up devices in a SharePoint list, shows lettered options with details and a photo, asks about extra requirements, confirms the request, and then sends it to IT.

## What I changed from the lab

- Matched the device skill to my own SharePoint **Devices** list: Title, Model, Asset type, Manufacturer, Color, Purchase price, Condition notes, Status and Device photo.
- Showed purchase price as currency, and kept serial number, order number and owner fields out of what employees see.
- Built the email step as a Power Automate flow: requester name, manufacturer, model, a link to the item in SharePoint, and the employee's comment. The flow runs in four steps: When an agent calls the flow, Get Device from SharePoint, Send an email in Outlook, and Respond to the agent.
- Fixed a Choice column showing as raw data in the email by using the column's Value.
- Added a rule so the agent never treats an attachment file name as an image link.

## Screenshots

| | |
|---|---|
| `01` | Agent configuration: instructions, skills, tools and knowledge |
| `02` | The Devices list in SharePoint that the agent reads from |
| `03` | Catalog lookup with lettered options and photos |
| `04` | Choosing an option and adding a requirement |
| `05` | Request summary, confirmation and submission |
| `06` | The email IT receives |
| `07`-`10` | Troubleshooting an Outlook problem from first message to resolution |
| `11` | The Power Automate flow behind the device request email |

## Tools

Microsoft Copilot Studio, SharePoint Lists, Power Automate, Outlook connector.

## Not included

I kept the exported flow and agent files out of this repo because they contain tenant details. Screenshot 11 shows the flow steps, and the screenshots and skill files show how it works.

## What I learned

_Add your own notes here, in your own words._
