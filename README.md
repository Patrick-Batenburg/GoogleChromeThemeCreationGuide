# Theme Creation Guide
For Google Chrome



  
# Table of Contents
- [Manifest File Format](#manifest-file-format)
- [Image dimensions](#image-dimensions)
- [Image Elements](#image-elements)
- [Color Elements](#color-elements)
- [Tint Elements](#tint-elements)
- [Property Elements](#property-elements)
- [Description of Elements](#description-of-elements)
  - [Basic Theme Elements](#basic-theme-elements)
    - [Image Elements](#image-elements-1)
      - [theme_frame](#theme_frame)
      - [theme_ntp_background](#theme_ntp_background)
      - [theme_tab_background](#theme_tab_background)
      - [theme_toolbar](#theme_toolbar)
  - [Advanced Theme Elements](#advanced-theme-elements)
    - [Image Elements](#image-elements-2)
      - [theme_button_background](#theme_button_background)
      - [theme_frame_inactive](#theme_frame_inactive)
      - [theme_frame_incognito](#theme_frame_incognito)
      - [theme_frame_incognito_inactive](#theme_frame_incognito_inactive)
      - [theme_frame_overlay](#theme_frame_overlay)
      - [theme_frame_overlay_inactive](#theme_frame_overlay_inactive)
      - [theme_ntp_attribution](#theme_ntp_attribution)
      - [theme_tab_background_incognito](#theme_tab_background_incognito)
      - [theme_tab_background_v](#theme_tab_background_v)
      - [theme_window_control_background](#theme_window_control_background)
    - [Color Elements](#color-elements-1)
      - [bookmark_text](#bookmark_text) 
      - [button_background](#button_background)
      - [control_background](#control_background)
      - [frame](#frame)
      - [frame_inactive](#frame_inactive)
      - [frame_incognito](#frame_incognito)
      - [frame_incognito_inactive](#frame_incognito_inactive)
      - [ntp_background](#ntp_background)
      - [ntp_header](#ntp_header)
      - [ntp_link](#ntp_link)
      - [ntp_link_underline](#ntp_link_underline)
      - [ntp_section](#ntp_section)
      - [ntp_section_link](#ntp_section_link)
      - [ntp_section_link_underline](#ntp_section_link_underline)
      - [ntp_section_text](#ntp_section_text)
      - [ntp_text](#ntp_text)
      - [tab_background_text](#tab_background_text)
      - [tab_text](#tab_text)
      - [toolbar](#toolbar)
    - [Tint Elements](#tint-elements-1)
      - [buttons](#buttons)
      - [frame](#frame)
      - [frame_inactive](#frame_inactive)
      - [frame_incognito](#frame_incognito)
      - [frame_incognito_inactive](#frame_incognito_inactive)
      - [background_tab](#background_tab)
    - [Property Elements](#property-elements-1)
      - [ntp_background_alignment](#ntp_background_alignment)
      - [ntp_background_repeat](#ntp_background_repeat)
      - [ntp_logo_alternate](#ntp_logo_alternate)
- [Packaging](#packaging)
  - [Creating a package](#creating-a-package)
  - [Updating a package](#updating-a-package)
  - [Uploading a previously packaged extension to the Chrome Web Store](#uploading-a-previously-packaged-extension-to-the-chrome-web-store)
  - [Packaging at the command line](#packaging-at-the-command-line)  
  - [Package format and scripts](#package-format-and-scripts)  

#  Manifest File Format
```json
{
    "manifest_version": 2,
    "name": "My Extension",
    "version": "versionString",
    "description": "A plain text description",
    "icons": {
        "16": "images/icons/icon16.png",
        "48": "images/icons/icon48.png",
        "128": "images/icons/icon128.png"
    },
    "author": "Name|Username|Nickname",
    "theme": {
        // Pick image elements your gonna use (or none). Name of images can be anything.
        "images": {
            "theme_button_background": "images/theme_window_control_background.png",
            "theme_frame": "images/theme_frame.png",
            "theme_frame_inactive": "images/theme_frame.png",
            "theme_frame_incognito": "images/theme_frame.png",
            "theme_frame_incognito_inactive": "images/theme_frame.png",
            "theme_frame_overlay": "images/theme_frame_overlay.png",
            "theme_frame_overlay_inactive": "images/theme_frame_overlay_inactive.png",
            "theme_ntp_attribution": "images/theme_ntp_attribution.png",
            "theme_ntp_background": "images/theme_ntp_background1920x1080.png",
            "theme_tab_background": "images/theme_tab_background.png",
            "theme_tab_background_incognito": "images/theme_tab_background.png",
            "theme_tab_background_v": "images/theme_tab_background_v.png",
            "theme_toolbar": "images/theme_toolbar.png",
            "theme_window_control_background": "images/theme_window_control_background.png"
        },
        // Pick color elements your gonna use (or none). Colors are in RGB format.
        "colors": {
            "bookmark_text": [0, 0, 0],
            "button_background": [0, 0, 0],
            "control_background": [0, 0, 0],
            "frame": [0, 0, 0],
            "frame_inactive": [0, 0, 0],
            "frame_incognito": [0, 0, 0],
            "frame_incognito_inactive": [0, 0, 0],
            "ntp_background": [0, 0, 0],
            "ntp_header": [0, 0, 0],
            "ntp_link": [0, 0, 0],
            "ntp_link_underline": [0, 0, 0],
            "ntp_section": [0, 0, 0],
            "ntp_section_link": [0, 0, 0],
            "ntp_section_link_underline": [0, 0, 0],
            "ntp_section_text": [0, 0, 0],
            "ntp_text": [0, 0, 0],
            "tab_background_text": [0, 0, 0],
            "tab_text": [0, 0, 0],
            "toolbar": [0, 0, 0, 0.0]
        },
        // Pick tint elements your gonna use (or none). Tints are in HSL format.
        "tints": {
            "buttons": [0.5, 0.5, 0.5],
            "frame": [0.5, 0.5, 0.5],
            "frame_inactive": [0.5, 0.5, 0.5],
            "frame_incognito": [ 0.5, 0.5, 0.5 ],
            "frame_incognito_inactive": [0.5, 0.5, 0.5],
            "background_tab": [0.5, 0.5, 0.5]
        },
        // Pick property elements your gonna use (or none).
        "properties": {
            "ntp_background_alignment": "center|stretch|top|top-left|top-right|bottom|bottom-left|bottom-right",
            "ntp_background_repeat": "no-repeat|repeat|repeat-x|repeat-y",
            "ntp_logo_alternate": 0
        }
    }
}
```


# Image dimensions
Recommended image elements dimensions.

*Image elements are defined under the "images" section in the manifest.json file.*
| Parameters                        | Recommended W x H                             |
| --------------------------------- | --------------------------------------------- |
| "theme_button_background"         | 30 x 30                                       |
| "theme_frame"                     | ∞ x 128                                       |
| "theme_frame_inactive"            | ∞ x 128                                       |
| "theme_frame_incognito"           | ∞ x 128                                       |
| "theme_frame_incognito_inactive"  | ∞ x 128                                       |
| "theme_frame_overlay"             | 1100 x 64                                     |
| "theme_frame_overlay_inactive"    | 1100 x 64                                     |
| "theme_ntp_attribution"           | Any but not too large                         |
| "theme_ntp_background"            | Recommended Minimum Size for images 800 x 600 |
| "theme_tab_background"            | 16 x 16 / 48 x 48 / 128 x 128                 |
| "theme_tab_background_incognito"  | ∞ x 128                                       |
| "theme_tab_background_v"          | ∞ x 128                                       |
| "theme_toolbar"                   | ∞ x 128                                       |
| "theme_window_control_background" | ∞ x 128                                       |

# Image Elements
Images should generally be in PNG format, because PNG has the best support for transparency. They can, however, be in any format supported by WebKit, including BMP, GIF, and JPEG.

*Image elements are defined under the "images" section in the manifest.json file.*
| #     | Description                                                                       | manifest.json Notation            |
| ----- | --------------------------------------------------------------------------------- | --------------------------------- |
| 1.    | The background of all the toolbar buttons.                                        | "theme_button_background"         |
| 2.    | The frame of the chrome browser/the area that is behind the tabs.                 | "theme_frame"                     |
| 2.1   | The same area as above, only that this represents the inactive state.             | "theme_frame_inactive"            |
| 2.2   | The same area under the incognito mode, when the window is active.                | "theme_frame_incognito"           |
| 2.3   | The same area but in the incognito mode, when the window is inactive.             | "theme_frame_incognito_inactive"  |
| 3.    | This is the image that appears at the top left of the frame.                      | "theme_frame_overlay"             |
| 3.1   | The same area as above, only that this represents the inactive state.             | "theme_frame_overlay_inactive"    |
| 4.    | This is the image that will be displayed in the 'theme created by' section.       | "theme_ntp_attribution"           |
| 5.    | This is the theme's inner background-the large white space is covered by this.    | "theme_ntp_background"            |
| 6.    | This is the area that covers the tabs that are not active.                        | "theme_tab_background"            |
| 6.1   | The same area under the incognito mode.                                           | "theme_tab_background_incognito"  |
| 7.    | The same area under the Aero mode.                                                | "theme_tab_background_v"          |
| 8.    | This represents both the current tab and the toolbar together.                    | "theme_toolbar"                   |
| 9.    | The background for the window control buttons (close, maximize, etc.,)            | "theme_window_control_background" |

# Color Elements
Colors are entered as RGB values, some elements can contain opacity value also. e.g. ```json "ntp_section": [15, 15, 15, 0.6] ```

*Color elements are defined under the "colors" section in the manifest.json file.*
| #     | Description                                                           | manifest.json Notation        |
| ----- | --------------------------------------------------------------------- | ----------------------------- |
| 10.   | The color of the bookmark element’s tekst.                            | "bookmark_text"               |
| 11.   | The background color of all the toolbar buttons.                      | "button_background"           |
| 12.   | The color of the window control buttons (close, maximize, etc.)       | "control_background"          |
| 13.   | The color of the frame, that covers the smaller outer frame.          | "frame"                       |
| 13.1  | The color of the same element, but in inactive mode.                  | "frame_inactive"              |
| 13.2  | The color of the same element, but in incognito mode.                 | "frame_incognito"             |
| 13.3  | The color of the same element, but in incognito, inactive mode.       | "frame_incognito_inactive"    |
| 14.   | The theme's inner background color.                                   | "ntp_background"              |
| 15.   | The color of the section frames when mouse over.                      | "ntp_header"                  |
| 16.   | The color of the links that appear in the background area.            | "ntp_link"                    |
| 16.1  | The color of the underline of all links in the background area.       | "ntp_link_underline"          |
| 17.   | The color of Recently closed tabs area's bg and frame of quick links. | "ntp_section"                 |
| 17.1  | The color of the links that appear in the section area.               | "ntp_section_link"            |
| 17.2  | The color of underline of links in the section area.                  | "ntp_section_link_underline"  |
| 17.3  | The color of text in the section.                                     | "ntp_section_text"            |
| 18.   | The color of all the text that comes in the inner background area.    | "ntp_text"                    |
| 19.   | The color of text, in the title of all inactive tabs.                 | "tab_background_text"         |
| 20.   | The color of text, in the title of current tab.                       | "tab_text"                    |
| 21.   | The color of the toolbar background.                                  | "toolbar"                     |

# Tint Elements
Tint elements change the hue, saturation and lightness of images.

*Tint elements come under the "tints" section in the manifest.json file.*
| #     | Description                                                           | manifest.json Notation        |
| ----- | --------------------------------------------------------------------- | ----------------------------- |
| 22.   | The color tint that can be applied to various buttons in chrome.      | "buttons"                     |
| 23.   | The color tint that can be applied to the frame of chrome.            | "frame"                       |
| 23.1  | The color tint that is applied when the chrome window is inactive.    | "frame_inactive"              |
| 23.2  | The color tint to the frame-in incognito mode.                        | "frame_incognito"             |
| 23.3  | Same as above, but when the window is inactive and in incognito mode. | "frame_incognito_inactive"    |
| 24    | The color tint of the inactive tabs in incognito mode.                | "background_tab"              |

# Property Elements
Property elements change the properties of images about how they are displayed.

*Property elements come under the "properties" section in the manifest.json file.*
| #     | Description                                                           | manifest.json Notation        |
| ----- | --------------------------------------------------------------------- | ----------------------------- |
| 25.   | The property that tells the alignment of the inner backrground image. | "ntp_background_alignment"    |
| 26.   | This property specifies if the above background should be repeated.   | "ntp_background_repeat"       |
| 27    | This lets you select the type of google chrome header you want.       | "ntp_logo_alternate"          |

# Description of Elements
## Basic Theme Elements
These elements are the starting point, by using only them, you can quickly create a basic theme.

### Image Elements
#### theme_frame
This image represents the area behind the tabs. There is no strict dimensions for this image, the rest of the area in the frame that is not covered by this image is covered by the color element frame. It would be helpful to know that this image by default repeats along the x-axis. Hence if you create a small square image, it will be automatically repeated along x-axis-which means you can create patterns if you use short sized images.

Remember this image doesn't repeat along-y, hence make sure it is long enough to cover the toolbar area-anything over 80px height is good, usually with grading alpha transparency at the bottom so that the image blends with the `json "frame"` color. (you can create a large sized frame image, that extends and coveres the frame borders too)

Else you might see a small seperation to the extreme top left of the frame, when the window is in restored mode due to the wrong size of the image.

Alternatively one can decide to create an image with width-long enough that the image repetition is not seen-this method allowes you to create one continuous design for the frame-but this method might slow down the loading time of the theme since large resolution screens require image of larger width (or else you'll see the repetition of the image). Note that if you don't include this image, the default frame of chrome is displayed, the color element  `json "frame"` doesn't override this.

#### theme_ntp_background
This is the image that is displayed at the large white space in the browser, in the new tab page, it can contain a background image that contains alpha transparency. Note that the notation ntp represents new tab page, hence all elements which contain ntp in the notation will correspond to some element inside the new tab page.

There are two ways you can create the inner background for the browser-use a large image without repetition/tiling or use a small image that repeats in x-axis and/or y-axis. (see `json "ntp_background_repeat"`).

There is also option for you to select the alignment of this image, by default the image is center aligned, but you may choose to align it the way you want. (see `json "ntp_background_alignment"`).

#### theme_tab_background
This is an image, this represents the tabs - all the inactive tabs.

Usually a less saturated image of `json "theme_toolbar"` is used for this. You may also design something else, but make sure that the design enables the user to distinguish the inactive tabs from the active one! This image also tiles default in x-axis and the height of this can be around 65p, the width is up to you.

#### theme_toolbar
This is an image that covers the area of the current tab and the toolbar below it. For older versions of Google Chrome, make sure this image is over 119px in height because the find bar (which appears when you press Ctrl+F ) shares the tool bar image, the width is up to you. Similar to the `json "theme_frame"`, this image also tiles along the x-axis so you have the option to create pattern or create a long width image for the toolbar. Remember that the toolbar contains some buttons and when the bookmarks are visible (CMD+B or Ctrl+B), they too occupy space in the toolbar.

So don't make the design too much crowded, or else the toolbar will not be visually appealing. Usually for the toolbar, a square, tiling image is preferred, which might be a gradient or just plain color.


## Advanced Theme Elements
Use these to create a more advanced theme.

### Image Elements
#### theme_button_background
This is the image that specifies the background for various buttons (stop, refresh, back, forward, etc..) in the toolbar. This image is optional, if you do not include this image, the color element `json "button_background"` overrides the button's background color.

#### theme_frame_inactive
This is an image, representing the area behind the tabs, when the chrome window is out of focus/inactive.

All that is applicable to `json "theme_frame"`, applies to this. Usually to avoid making the theme heavy, you can go for `json "frame_inactive"` tint, to show that the window is inactive-it's efficient than creating a whole new image. But it's up to the designer to decide, if it's going to be an image seperately for the inactive state or there is going to be a color tint when the window is inactive.

#### theme_frame_incognito
This is similar to the `json "theme_frame"`, but this image represents the frame of a window in incognito mode. You may choose to redesign the image specially for the incognito mode or ignore this, so that whatever you made for `json"theme_frame"` will be tinted (see `json "frame_incognito"`) and used in incognito mode (it's by default that it gets a dark tint in incognito mode).

#### theme_frame_incognito_inactive
This is also an image, similar to `json "theme_frame_inactive" `, but this image is for the inactive frame of a window in incognito mode (see `json "frame_incognito_inactive"`).

#### theme_frame_overlay
This is the image that will be displayed at the top left corner of the frame, over the `json "theme_frame"` image. Also this image doesn't repeat by default. Hence this image may be used in case you don't want the frame area design to repeat. Similar to the `json "theme_frame" `, anything over 80px height is good, usually with grading alpha transparency at the bottom so that the image blends with the `json "frame" ` color.

#### theme_frame_overlay_inactive
This is similar to `json "theme_frame_overlay"`, but will be displayed when the browser window is inactive. If you do not include this image, `json "theme_frame_overlay"` image will be darkly tinted and used by default-to denote the inactive frame.

#### theme_ntp_attribution
#### theme_tab_background_incognito
#### theme_tab_background_v
#### theme_window_control_background

### Color Elements
#### bookmark_text
#### button_background
#### control_background
#### frame
#### frame_inactive
#### frame_incognito
#### frame_incognito_inactive
#### ntp_background
#### ntp_header
#### ntp_link
#### ntp_link_underline
#### ntp_section
#### ntp_section_link
#### ntp_section_link_underline
#### ntp_section_text
#### ntp_text
#### tab_background_text
#### tab_text
#### toolbar

### Tint Elements
#### buttons
#### frame
#### frame_inactive
#### frame_incognito
#### frame_incognito_inactive
#### background_tab
#### Property Elements
#### ntp_background_alignment
#### ntp_background_repeat
#### ntp_logo_alternate

# Packaging
## Creating a package
## Updating a package
## Uploading a previously packaged extension to the Chrome Web Store
## Packaging at the command line
## Package format and scripts
