# Changes based on feedback.

## 2023-05-23

Somewhere in the introduction of default colours, we lost one premise of IMSC, and got confused over defaults.

To address this, we've modified the use of some default styles.

Therefore ALL regions must have r_default, ALL divs must have d_default, and these in turn reference _r_default and _d_default.  And _r_default and _d_default must not be referenced by regions or styles.

Also, _r_quantisationregion is introduced, as we need some way to store the quantisation intent more explicitly, and outside of things we may consider to be for a different reason.  _r_quantisationregion must never be referenced, but always be present.  tts:extent and tts:origin have been removed from r_default as they msut always be present on each region.

These changes will require code changes to existing implementations, but we're getting close now with good feedback from implementors.

Please use [the updated imsc-rosetta-qualify](https://imsc-rosetta.github.io/imsc-rosetta-qualify/) to help you get the files correct, and visit styles.md

Added tts:luminanceGain in _r_default

Added more explanation of line quantisation in styles.md

Added `tts:overflow="visible"` to `r_region`.  Note that subtitles should not generally exceed region sizes, but it is noted that when using p_shear, it may cause a p to extend beyond the region bounds.  Players/renderes may not honour drawing outside fo the region bounds.

Update samples and rebuilt sample descriptive files, including image re-render.


## 2023-05-17 - ps_shear

`ps_shear` renamed to `p_shear`, as tts:shear cannot be applied to `span`

Updated samples and documentaiton to reflect the change.

re-introduce p_al_center, and allow p_al_xxx to be set in style on _r_default and _r_vertical to set default alignment/justification on horizontal and vertical regions.

Be more explicit about what you may modify.

## 2023-05-12 - default foreground colour

Added s_fg_white as defaulting to full-white (#FFFFFF) and use in _r_default

For off-white, s_fg_white may be changed, e.g. to #EEEEEE.

Moved `tts:wrapOption="noWrap"` from _r_default to the non-modifiable r_default

Remove tts:color="white" from r_default, replace with a requirmeent to have a color style mentioned in _r_default

Note: to set a different overall default foreground colour, set (for example) style="s_fg_yellow" in _r_default

Small corrections and added explanation.

Remove _p_default and _s_default from the FAQ.

Modified sample files to reflect the changes.

Add p_al_center back in to the style names set.

Allow style in _r_region to contain an alignment p_al_xxxx as a default alignment.

Add _r_vertical as a holder for (changeable) default vertical styles.  The style attirbute may contain an alignment p_al_xxxx as a default alignment for vertical text.