# 3isogdescent1
FindSubspace(S3, pred) is not used at all, vibe coded with ChatGPT on June 8, 2026.

Substitute your current 3isogdescent.m file inside the folder /usr/local/magma/package/Geometry/CrvEll/ThreeDesc/
If necessary, "touch" this file to have the date of the original 3isogdescent.m, e.g.:
[code]touch -t 202310251430.00 3isogdescent.m[/code] for October 25, 2023, at 2:30 PM

I sent this code to Magma for review by email on June 25, 2026. No response from them yet.

**EDIT**: filed a bug report on July 11, 2026 via https://github.com/Magma-Maths/Magma (John Voight provided a link in his ANTS XVII slides https://www.antsxvii.org/slides/antsxvii-voight-slides.pdf).

To be clear, it is not my code. It was ChatGPT's idea to stop using FindSubspace, and it is ChatGPT's implementation of that idea. The ~20,000 times speedup and close to no RAM use may be achieved by commenting a call to FindSubspace and using lines 80-98 instead (although the attached *.m file probably went through other minor changes, too).

The code makes ThreeIsogenySelmerGroups (and all intrinsics dependant on it) much faster (~20,000 times) for the elliptic curves _with rational 3-torsion points_ (Z/3Z, Z/6Z, Z/9Z, Z/12Z, Z/2ZxZ/6Z), their isogenous curves (even those of trivial torsion) and their quadratic twists (even those of trivial torsion). It is also observably faster for Mordell curves of trivial torsion. In all cases, unlike the original ThreeIsogenySelmerGroups, this modified code consumes close to no RAM.

This modified 3isogdescent.m estimates 3-ranks of rank 10-17 Mordell curves of _trivial torsion_ in a very reasonable time, from 1 second to 40 minutes each (4 minutes on average, test case bank of 143 curves), with much time spent on local conditions and only ~20+20 seconds spent on the modified FindSubspace step (called once for the curve and once for the 3-isogenous curve).

Since recently, I am also planning to look at the general 3selmer.m Magma code for a full 3-descent. It seems that a lot of black-box is-it-a-perfect-cube guessing is still happening there, which seems to slow it down significantly (although Magma developers recently told me that everything is as fast as it can be there).
