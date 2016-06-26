# scss-grid-gen

> Dead simple (perhaps too simple) grid-mixins for Sass

*NOTE: This repository is meant to go hand-in-hand with a [blog post](http://scottyeck.com) I'm writing about best practices when building a tool that exposes an API in Sass. That said, it will be available for use as well, so feel free!*

## Installation

```bash
$ npm install scss-grid-gen --save-dev 
```

## Usage

Once installed, import the module.

```scss
@import "node_modules/scss-grid-gen/core";
```

You can now use the core-mixins as desired.

### Recommended Usage

Once imported, this library can be used in a variety of ways to suit the needs of the consumer.

#### Option 1: Zero-customization

To use _scss-grid-gen_ with absolutely no customization at all, simply call the `grid-gen-declarations()` mixin after the module has been imported.

```scss
@import "node_modules/scss-grid-gen/core";

@include grid-gen-declarations();
```

Doing so will output all CSS declarations pertaining to the included grid, using all default settings.

#### Option 2: Overriding Defaults

The easiest way to customize _scss-grid-gen_ is to override the default variables before they are consumed by `grid-gen-declarations()`.

```scss
$grid-gen-max-width: 		90rem;
$grid-gen-gutter-width: 	1.5rem;
$grid-gen-column-count: 	24;

$grid-gen-container-class: 	"grid-container";
$grid-gen-row-class: 		"row";
$grid-gen-column-class: 	"col";
$grid-gen-column-class: 	"col-";

@import "node_modules/scss-grid-gen/core";

@include grid-gen-declarations();
```

This will output all CSS from `grid-gen-declarations()` using the settings configured prior to the import. See below for more information regarding the variables whose values can be modified.

Note that you must define the variables _before_ the module itself is imported. This is due to the way in which `!default` variable declarations operate in Sass. Read Edwin Morris' [article on the topic](https://robots.thoughtbot.com/sass-default) for more info.

#### Option 3: DIY

Should you wish to do so, you may use the individual building-blocks from `scss-grid-gen` to build your own grid. See below for Funciton/Mixin API documentation, and be sure to check out the examples.

##### Configurable Defaults

###### Measurement Configuration

| var  							| description								|
|:--							|:--										|
| `$grid-gen-max-width`   		| Max-width of grid-container element 		|
| `$grid-gen-gutter-width`  	| Width of gutter between grid-columns 		|
| `$grid-gen-flow-direction`  	| Direction from which the grid should flow |
| `$grid-gen-column-count`  	| Number of columns the grid should span	|

###### Selector Configuration

| var								| description
|:--								|:--
| `$grid-gen-container-class`		| Class for grid-container element		|
| `$grid-gen-row-class`				| Class for grid-row element			|
| `$grid-gen-column-class`			| Class for grid-column element			|
| `$grid-gen-column-class-prefix`	| Prefix for grid-column span class		|

## Function/Mixin API

For now, see [`_grid-gen.scss`](./src/_grid-gen.scss) for inline API documentation. Don't be scared - it's only a few mixins.