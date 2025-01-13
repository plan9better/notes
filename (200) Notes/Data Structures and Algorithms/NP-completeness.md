**NP-Completeness** is a concept in [[Computational Complexity Theory|complexity theory]]. It deals with how hard it is to solve certain types of problems on a computer.

In short, problems in the class [[NP (computational complexity)|NP]] can be checked quickly if you have a potential solution, but we don’t know how to solve them quickly in the first place. A problem is **NP-Complete** if:

1. It’s in NP (meaning solutions can be verified quickly).
2. Every other NP problem can be transformed into it (called a [[Reduction (complexity)|reduction]]).

If a fast algorithm (called [[Polynomial Time|P time]]) is found for one NP-Complete problem, all NP problems would become easy to solve quickly too, but we don’t know if such an algorithm exists. This is related to the big unsolved question: [[P vs NP|P vs NP problem]].