# AssetImgSize

Liquid filter which convert asset path to image size parameter.

## Installation

Just copy _plugins directory to your jekyll site root or just copy asset_img_size.rb to your _plugins directory if it's already exist.

## Usage

Image file **MUST** format in `filename_widthxheight.extension`, and size formula must be the **LAST** one, extension don't matter.
Then you'll get output in **array**, use `{{ output | first }}` and `{{ output | last }}` to get width and height.

In my case, I'll use them in `style="max-width: {{ output | first }}; max-height: {{ output | last }};"`, so I can have more flexibility to control img and video style.

#####Correct filename example

[x] `myimage_300x300.jpg`

[] `myimage.jpg` return nil

[] `myimage_300x300_game.jpg` return nil

[x] `myimage_100x100_300x300.jpg` it'll still take last one

[x] `myimage_x300.jpg`

[x] `myimage_300x.jpg`

##### Input

    {{ 'assets/img/projects/myproject/image-1_300x400.jpg' | asset_img_size }}
	{{ 'assets/img/projects/myproject/image-1_x400.jpg' | asset_img_size }}
	{{ 'assets/img/projects/myproject/image-1_300x.jpg' | asset_img_size }}

##### Output
You'll get output in array

    300px400px
	100%400px
	300px100%

## GitHub Pages not support plugins

GitHub pages disable custom plugins for security reasons, so you have to use this plugin locally.

## License

Copyright (c) 2017 Jon Gao, under the terms of the MIT License.