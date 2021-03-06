# How to Use

All you need to create a kit is the following HTML structure. Simply replace the team class with the appropriate class. See below for a full list of team classes.

```
<div class="kit wigan-athletic_1617">
	  <div class="kit-base"></div>
	  <div class="kit-layer-1"></div>
	  <div class="kit-layer-2"></div>
	  <div class="kit-layer-3"></div>
	  <div class="kit-layer-4"></div>
	  <div class="kit-layer-5"></div>
	  <div class="kit-layer-6"></div>
	  <div class="kit-layer-7"></div>
	  <div class="kit-layer-8"></div>
	  <div class="kit-detail"></div>
	  <div class="kit-collar"></div>
</div>
```

# Team Classes

**Premier League**

- afc-bournemouth_1617
- arsenal_1617
- burnley_1617
- chelsea_1617
- crystal-palace_1617
- everton_1617
- hull-city_1617
- leicester-city_1617
- liverpool_1617
- manchester-city_1617
- manchester-united_1617
- middlesbrough_1617
- southampton_1617
- stoke-city_1617
- sunderland_1617
- swansea-city_1617
- tottenham-hotspur_1617
- watford_1617
- west-bromwich-albion_1617
- west-ham-united_1617

**English Football League Championship**

- aston-villa_1617
- barnsley_1617
- birmingham-city_1617
- blackburn-rovers_1617
- brentford_1617
- brighton-and-hove-albion_1617
- bristol-city_1617
- burton-albion_1617
- cardiff-city_1617
- derby-county_1617
- fulham_1617
- huddersfield-town_1617
- ipswich-town_1617
- leeds-united_1617
- newcastle-united_1617
- norwich-city_1617
- nottingham-forest_1617
- preston-north-end_1617
- queens-park-rangers_1617
- reading_1617
- rotherham-united_1617
- sheffield-wednesday_1617
- wigan-athletic_1617
- wolverhampton-wanderers_1617

**English Football League One**

- afc-wimbledon_1617
- bolton-wanderers_1617
- bradford-city_1617
- bristol-rovers_1617
- bury_1617
- charlton-athletic_1617
- chesterfield_1617
- coventry-city_1617
- fleetwood-town_1617
- gillingham_1617
- millwall_1617
- milton-keynes-dons_1617
- northampton-town_1617
- oldham-athletic_1617
- oxford-united_1617
- peterborough-united_1617
- port-vale_1617
- rochdale_1617
- scunthorpe-united_1617
- sheffield-united_1617
- shrewsbury-town_1617
- southend-united_1617
- swindon-town_1617
- walsall_1617

**English Football League Two**

- accrington-stanley_1617
- barnet_1617
- blackpool_1617
- cambridge-united_1617
- carlisle-united_1617
- cheltenham-town_1617
- colchester-united_1617
- crawley-town_1617
- crewe-alexandra_1617
- doncaster-rovers_1617
- exeter-city_1617
- grimsby-town_1617
- hartlepool-united_1617
- leyton-orient_1617
- luton-town_1617
- mansfield-town_1617
- morecambe_1617
- newport-county_1617
- notts-county_1617
- plymouth-argyle_1617
- portsmouth_1617
- stevenage_1617
- wycombe-wanderers_1617
- yeovil-town_1617

The goalkeeper kits are achieved by adding the class '.GK' to the 'kit' layer like so:

```
<div class="kit wigan-athletic_1617 GK">
	  ...
</div>
```

# Using SASS

Inside the /src/sass folder you'll find the following files:

```
style.scss

The master file from which to compile
```

```
variables.scss

Contains a list of global variables
```

```
colours.scss

Contains a list of colour variables
```

```
kit-templates.scss

The master file containing the base styles for the kits
```

```
kitfont.scss

Contains all the font mappings
```
```
kits_1617.scss

Contains the styling for all 92 EPL/EFL teams
```

# Variables

Inside variables.scss there are 4 variables:

**$kit-size**

This is the master value which controls the base sizing of the font.

```
default = 80px
```

**$detail-visible**

Show or hide the content of the '.kit-detail' layer, effectively showing or hiding the team badge, sponsor and manufacturer. Ideal if you want to avoid licensing issues ;)

```
default = true
```
```
true = shows the kit detail
false = hides the kit detail
```

**$season**

Set the class names in accordance with the current season value. You can change or remove this value if you wish

```
default = 1617
```

**$img-path**

Sets the path to the image folder

```
default = '../img/'
```

# Adding Custom Kits

You can add as many kits as you like by simply adding your own SASS.

Each kit is made of the following layers: kit-base, kit-layer-1, kit-layer-2, kit-layer-3, kit-layer-4, kit-layer-5, kit-layer-6, kit-layer-7, kit-layer-8, kit-detail, kit-collar

You can also create unique goalkeeper styles by adding styles under the '.GK' class.

The layer structure of a kit is as follows:  

**.kit-base**  
Set the default base colour of the kit

**.kit-layer-(1|2|3|4|5|6|7|8)**  
A series of layers which are stacked on top of one another. Layer 1 is the 'bottom' layer, layer 8 is the 'top' layer.

**.kit-detail**  
Contains a PNG image of the kit detail (sponsor, badge, manufacturer)

```
If $detail-visible is set to 'false' the contents of this layer will not appear
```

**.kit-collar**  
Sets the collar style - there are currently 3 variants:  
- .kf-collar-base-round  
- .kf-collar-base-v  
- .kf-collar-base-v-2  

All you need to do to is extend the desired element and set the colour, eg:
```
@extend .kf-body-stripes-1, .kf-black;
```

An example of how to apply this to a team:

```
.your-team-name_#{$season} {
    .kit-base {
        @extend .kf-red-1;
    }
    .kit-layer-1 {
        @extend .kf-body-stripes-1, .kf-black;
    }
    .kit-detail {
        background-image:url('../img/kit-detail_#{$season}/detail-your-team-name_#{$season}.png');
    }
    .kit-collar {
      @extend .kf-collar-base-round, .kf-red-1;
    }
    &.GK {
        .kit-base {
            @extend .kf-dark-green-2;
        }
        .kit-detail {
        	background-image:url('../img/kit-detail_#{$season}/detail-your-team-name-gk_#{$season}.png');
    	}
        .kit-collar {
            @extend .kf-collar-base-round, .kf-dark-green-2;
        }
    }
}
```

You can refer to the demo page 'http://kitfont.chrislorton.com/components.html' to see the current available kit components and 'http://kitfont.chrislorton.com/colours.html' to see default list of colour values. 

# Compatibility 

- IE10+
- Chrome 21+
- Firefox 28+
- Safari 6.1+
- Opera 12+
- Edge 12+
- iOS 7+
- Android 4.4+

There is a known incompatability on certain kits that contain gradients when using non-Webkit browsers. During the 16/17 season this includes:  
- Coventry City
- Cheltenham Town
- Hartlepool United

By default (with $detail-visible set to 'true') this will not be an issue as the gradient effect is added to the .'kit-detail' PNG image. However, with $kit-detail set to 'false' the gradient effect is reproduced by using a font mask and a text-gradient which is currently only supported in Webkit browsers.

# Planned improvements

For the pedants out there (like me) - there are some slight inconsistencies with the positioning of some kit components, meaning there are occasional (very small) gaps between components. This is more noticeable the larger your kits are.

Also, the .kit-detail layer is slightly offset from the center, and as a result doesn't perfectly match the edges of the kit base layer. I aim to fix this very soon by resizing the kit images.

There are also quite a lot of missing GK kits in League One and League Two. Currently I have generic green GK kits for those teams for which I couldn't find any reference.

# Reference

http://kitfont.chrislorton.com/
