This are the steps I took to make my Toshiba Chromebook 2 (2014) Swanky behave properly:
(tested on solus)

# Fix the keyboard
## To make the search key (aka super as recognized by the kernel(?)) be an escape key
Add
```
key <LWIN> {        [Escape] };
```
to the end of the `xkb_symbols "basic" { }` block in `/usr/share/X11/xkb/symbols/us`, like this
```
xkb_symbols "basic" {
	// other shit, that no one really knows what it does

	key <LWIN> {        [Escape] };
}

```

Yes, it is weird that something that should be language independed goes to a langugage specific file. I know. Putting in `pc` as the other fix does NOT work. And yes, putting it on us works for other languages like bg, idk how.

## To make the media keys work as media keys by default, as F<N> otherwise
Add
```
key <FK01> { 	[XF86Back, NoSymbol, NoSymbol, NoSymbol, F1] 			};
key <FK02> { 	[XF86Forward, NoSymbol, NoSymbol, NoSymbol, F2] 		};
key <FK03> { 	[XF86Refresh, NoSymbol, NoSymbol, NoSymbol, F3] 		};
key <FK04> { 	[Print, NoSymbol, NoSymbol, NoSymbol, F4] 			};
key <FK05> { 	[Super_L, NoSymbol, NoSymbol, NoSymbol, F5] 			};
key <FK06> { 	[XF86MonBrightnessDown, NoSymbol, NoSymbol, NoSymbol, F6] 	};
key <FK07> { 	[XF86MonBrightnessUp, NoSymbol, NoSymbol, NoSymbol, F7] 	};
key <FK08> { 	[XF86AudioMute, NoSymbol, NoSymbol, NoSymbol, F8] 		};
key <FK09> { 	[XF86AudioLowerVolume, NoSymbol, NoSymbol, NoSymbol, F9] 	};
key <FK10> { 	[XF86AudioRaiseVolume, NoSymbol, NoSymbol, NoSymbol, F10] 	};

key <UP>   {	[  Up, Page_Up			]	};
key <LEFT> {	[  Left, Home			]	};
key <DOWN> {	[  Down, Page_Down		]	};
key <RGHT> {	[  Right, End		        ]	};
```
to the end of the `xkb_symbols "editing" { }` block in `/usr/share/X11/xkb/symbols/pc`, like this
```
xkb_symbols "editing" {
	// other shit, that no one really knows what it does

	// that shit I just showed you
}

```

## recommended
make escape+alt change the current language

# To fix the audio output
TODO
Not done yet, but people on the interwebz reported it is possbile.
Look into baytrail audio fixes(ucm files and whatnot) or https://github.com/fascinatingcaptain/CBFixesAndTweaks.

# Fix the audio input
Idk, haven't done it, haven't seen anybody do it either. Good luck. Don't forget to ping me if you succeed.
