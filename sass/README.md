
@mixin respond-above ($breakpoint) {
    // If breakpoint exists in the map
  @if map-has-key($breakpoints, $breakpoint) {
    // Get the breakpoint value.
    $breakpoint-value: map-get($breakpoints, $breakpoint);
    //The media query.
    @media (min-width: $breakpoint-value){
      @content;
    }
    // If the breakpoint does not exist.
  } else {
      // Log a warning
      @warn 'invalid breakpoint: #{$breakpoints}.';
    }
  
}

*/

@include transform(top-right, translate(-150px, 150px),  translate(20px, -20px), translate(0, 0) );


@include transform(left, translateX(150px),  translateX(-20px), translateX(0) );



@mixin transform($move-to, $initial-value, $custom-value, $final-value ) {
  @if $move-to == top {
    @content;
  } 
  @if $move-to == top-right {
    @content;
  }
  @if $move-to == top-small {
    @content;
  }
  @if $move-to == left {
    @content;
  }
    
  @keyframes move-#{$move-to} {
    0% {
      opacity: 0;
      transform: $initial-value;
    }
    80% {
      transform: $custom-value;
    }
    100% {
      opacity: 1;
      transform: $final-value;
    }
  }
  else {
    @warn 'invalid transform: ' #{$move-to};
  }
}

