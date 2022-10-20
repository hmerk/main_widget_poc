![image|281x499](upload://nitRXgB1FilYG47fEdVOZjlurvn.jpeg)

This projects overall aim is to provide a unique view on mobile devices without the need of complex configuration.
To achieve this "zero config" approach, one will need a well maintained semantic model with some prerequisits, which will be described in the individual sub widget documentations.
One thing in common is the use of uiSemantics for labeling the shown equipment. Background and usage of the uiSemantics can be found in this topic
Benefit of using the semantic model is to not have to modify any wdgets if new supported stuff is added, but just set those up correctly in the model.
Even removing devices does not need reconfiguration.




The "main_widget" project is a series of widgets to create a new mobile view for controlling your openHAB installation. For full functionality, you will need to install all widgets listed in the development thread.
https://community.openhab.org/t/oh3-main-ui-new-main-widget-development-and-testing-wip/138794/1

Installation:
- <s>Add the non semantic tag "Floor" to all your floors and if you like, also add the widgetOrderIndex to them</s>
- <s>Add the name of the floor group 8e.g. gGroundfloor) as a new non semantic tag to each room in that particular floor </s>
- If you want a specific ordering in the floors and/or rooms menu, please add the widgetOrderIndex as metadata to your items in the model.
- Install all needed widgets for this projekt from the marketplace.
- Create an new layout page in openHAB MainUI
- Enter the code tab for the new page and paste the following code

```javascript
config:
  label: openPage
  sidebar: true
  hideNavbar: true
  showFullscreenIcon: false
  hideSidebarIcon: true
  style:
    --f7-block-padding-horizontal: 0px
    --f7-navbar-height: 0
blocks:
  - component: oh-block
    config:
      stylesheet: |
        .block:first-child{
          margin-top: 15px;
          }
    slots:
      default:
        - component: oh-grid-row
          config: {}
          slots:
            default:
              - component: oh-grid-col
                config: {}
                slots:
                  default:
                    - component: widget:main_widget
                      config:
                        locationTitle:
                        scenesGroup:
                        securityGroup:
                        securityMode:
                        referencePIN:
masonry: null
grid: []

```

configure the main_widget on your new page with the missing information (some items/groups need to be definded.

## Screenshots

![image|281x499](upload://9pIPS4zAxCb6Ver7D3qzCg191Km.jpeg)
![image|281x499](upload://gSaDG9rNulm0jY5VRA9mJG1yg0U.png)

## Changelog
### Version 0.3
- fixed top and bottom spacing [@Nic0205]
- changed bottom tabs from button to oh link for further improvements [@Nic0205]
- refactored repeater usage to remove need of additional tags [@hmerk]
- code splitting, moved informationa middle part to separate widgets. [@hmerk]
### Version 0.3
- fixed menu sorting and coloring
- changed margins to better use screen space
### Version 0.2
- added menu entry sorting for floors and rooms [@Nic0205]
- new config options for scene and security group and security mode [@hmerk]
### Version 0.1
- initial release

