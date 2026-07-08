# 3isogdescent1
FindSubspace(S3, pred) is not used at all, vibe coded with ChatGPT on June 8, 2026.

Substitute your current 3isogdescent.m file inside the folder /usr/local/magma/package/Geometry/CrvEll/ThreeDesc/
If necessary, "touch" this file to have the date of the original 3isogdescent.m, e.g.:
touch -t 202310251430.00 3isogdescent.m for October 25, 2023, at 2:30 PM

I sent this code to Magma for review on June 25, 2026. No response from them yet.
To be clear, it is not my code. It was ChatGPT's idea to stop using FindSubspace, and it is ChatGPT's implementation of that idea. The only changed lines are 80-98.

The code makes ThreeIsogenySelmerGroups (and all intrinsics dependant on it) much faster for the elliptic curves with rational 3-torsion points (Z/3Z, Z/6Z, Z/9Z, Z/12Z, Z/2ZxZ/6Z, Z/2ZxZ/12Z), their isogenous curves (even of trivial torsion) and their quadratic twists (even of trivial torsion). It is also observably faster for Mordell curves of trivial torsion. In all cases, unlike the original ThreeIsogenySelmerGroups, this modified code consumes close to no RAM.

This modified 3isogdescent.m estimates 3-ranks of rank 14-17 Mordell curves of trivial torsion in a very reasonable time, say 2-3 minutes each, with most time spent on local conditions and only ~20 seconds spent on the modified FindSubspace step.

Since recently, I am also planning to look at the general 3selmer.m Magma code for a full 3-descent. It seems that a lot of black-box is-it-a-perfect-cube guessing is still happening there, which seems to slow it down significantly (although Magma developers recently told me that everything is as fast as it can be there).
