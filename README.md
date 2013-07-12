responsive
==========

Responsive Framework based on SASS

To create a responsive column, use @include column(3, no-margin-left), for example

@import "compass/css3";

@mixin column($colnum,$margin:margin) {
  width: get-width($colnum,$margin);
	@if $colnum != 12 {
		float:left;
	}
	@include box-sizing(border-box);
	@if $margin == 'no-margin' {
		margin-left:0;
		margin-right:0;
	}
	@else if $margin == 'no-margin-left' {
		margin-right:0.833333%;
		margin-left:0;
	}
	@else if $margin == 'no-margin-right' {
		margin-left:0.833333%;
		margin-right:0;
	}
	@else {
		margin-right:0.833333%;
		margin-left:0.833333%;
	}
	overflow:hidden;
	vertical-align:top;
	
}
@function get-width($colnum,$margin){
	@if $margin == 'no-margin' {
		@return ($colnum * 08.333333%);
	}
	@else if $margin == 'no-margin-left' or $margin == 'no-margin-right'{
		@return ((($colnum * 80) - 8) / 960) * 100%;
	}
	@else {
		@return ((($colnum * 80) - 16) / 960) * 100%;
	}
}
@function max($pixels) {
  @return 'max-width:'#{$pixels/16.0}'em'
}
@function min($pixels) {
  @return 'min-width:'#{$pixels/16.0}'em'
}

