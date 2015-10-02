# Storyous CSS developer .bootstrap {

## Table of Contents

1. [Less](#less)
1. [Less structure and files](#less-structure-and-files)
1. [File and directory description](#file-and-directory-description)
1. [Code Standards and the best practices](#code-standards-and-the-best-practices)
1. [Font icons](#font-icons)


## Less

**Less** is a CSS pre-processor that extends CSS with dynamic behavior such as variables, mixins, operations and functions.
[Less](http://lesscss.org/)



## Less structure and files

```javascript

    less/
    ├── vendor/
    ├── bootstrap/
    ├── components/
    ├── pages/
    ├── utilities/
    │   ├── mixins.less 
    │   └── fonts.less 
    ├── layout.less
    ├── global.less
    ├── variables.less
    └── main.less

   ```



## File and directory description

- **vendor**: directory for 3rd-party libraries such a lesshat.less, animations.less, jQuery-ui.less etc. These files must not be modified but you can overload these css rules in other files.
- **bootstrap**: directory for bootstrap less files.
- **components**: directory for less files describing components such a modal.less, carousel.less, contact-form.less etc.
- **pages**: directory for less files describing css rules for single pages. ( i.e. contact.less, homepage.less... )
- **utilities**:  directory containing mixins.less and fonts.less
- **mixins.less**: rules for less [mixins](https://github.com/Storyous/javascript)
- **font.less**:  rules for fonts and font icons
- **layout.less**: rules describing layouts parts such a header, footer, etc.
- **global.less**: rules for general content rules ( font-family definnition, h1 - h6 rules, link colors,...) 
- **variables.less**: file less variables such a viewport breakpoints, colors etc
- **main.less**: main file that imports all other less files




## Code Standards and the best practices

1. **One Rule = One Line**  ( mandatory for PAY project )
	```css
	
	//wrong
	.classname { border: 0; background: #FFF; } 
	
	//correct
	.classname { 
		background: #FFF;
		border: 0;
		color: #252525;
		float: left;
		margin: 0;
		padding: 0;
	}
	 ```
2. **One Selector = One Line**  ( mandatory for PAY project )
	```css
	
	//wrong
	html,body { margin:0; padding: 0 } 
	
	//correct
	body, 
	html {
		margin: #FFF;
		padding: 0;
	}
	
	 ```
3. **Indent the rules**
	```css
	
	//wrong
	html, 
	body { 
	margin:0; 
	padding: 0 
	} 
	
	//correct
	body, 
	html {
		margin: #FFF;
		padding: 0;
	}
	
	 ```
4. **Keep your class and ID names easy to follow**
5. **Try to keep nesting Deph under 6 level**




## Font icons (icomoon)

Icomoon is service that alllows to generate font-face pack from svg icons.

1. Create vector icon. Expand object's strokes and save it as svg
1. Go to [https://icomoon.io/app/](https://icomoon.io/app/) and import this icon to set
1. Edit icon and select it with select tool and go to selection and generate font.
1. Download the pack and copy content of font/ to public/fonts/icomoon/ in your web project
1. To this directory also copy **selection.json** which is needed for other set editation
1. Copy the font.css and insert it to public/less/utilities/fonts.less
1. Edit the css paths
1. Next time when you want to edit the set yout need to import selection.json to [https://icomoon.io/app/](https://icomoon.io/app/) and repeat the proccess




**[⬆ back to top](#table-of-contents)**


# };
