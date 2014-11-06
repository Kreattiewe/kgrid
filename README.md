# kgrid (v0.0.1)

One grid system to rule them all, based in gridle

## Quick start
  
Importing kgrid

```scss
import "kgrid/kgrid"
```

Configure your grid :

```scss
@include gridle_setup( (
  context : 12,
  gutter-width : 20px,
  direction : rtl,
  debug : true
  // etc...
) );
```

Register states (media queries) (optional) :

```scss
@include gridle_register_state ( mobile , (
  max-width : 480px 
) );
@include gridle_register_state ( tablet , (
  min-width : 481px,
  max-width : 1024px
) ) ;

// even with full custom queries :
@include gridle_register_state ( landscape, (
  query : "(orientation : landscape)"
) );
```

Generate all classes :

```scss
@include gridle_generate_classes();
```

Use your grid in html :

```markup
<div class="container">
  <div class="kgrid-12 hide-print">
    Header
  </div>
  <div class="kgrid-8 kgrid-mobile-12">
    Content
  </div>
  <div class="kgrid-4 kgrid-mobile-12 hide-print">
    Sidebar
  </div>
</div>
```

Or with mixins :

```scss
.container {
  @include kgrid_container();
  max-width:960px;
  margin:0 auto;
}
#header {
  @include kgrid(12);
}
#sidebar {
  @include kgrid(8);
  @include kgrid(12,  mobile );
}
#sidebar {
  @include kgrid(4);
  @include kgrid_hide( mobile );
}
@footer {
  @include kgrid(12);
}
```

Customize your content look and feel with Gridle mixins

```scss
#sidebar {
  background : red;

  @include kgrid_state(mobile) {
    background : green;
  }
}
```

## Generate custom classes

Gridle allows you to generate custom classes that will be available for each of your states. Here's an exemple

```scss
@include kgrid_generate_custom_class( ( 'center', '-', '%state' ) ) {
  text-align : center;
}
```

This will produce the classes : center, center-mobile, center-tablet and center-landscape automatically
