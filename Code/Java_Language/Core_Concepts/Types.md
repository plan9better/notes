#java, #type, #int, #long, #object, #float, #double
- end assignment with f or L to tell the compiler which you mean 
- You cant assign a int to a byte for example even if the  int variable value is small enough to fit in the byte.
- variable name must start with a letter, underscore, or a dollar sign $
- there are no object variables just object references
- you can only put dogs in an array of type dog but you can put a byte into an int array this is known as `IMPLICIT WIDENING`
# Primitive table
<table>
<thead>
<tr><td>Type</td><td>size</td><td>range</td></tr>
</thead>
<tr><td>boolean</td><td>JVM Specific</td><td>true or false</td></tr>
<tr><td>char</td><td>16 bit</td><td>0 - 65536</td></tr>
<tr><td>byte</td><td>8 bit</td><td>-128 - 127</td></tr>
<tr><td>short</td><td>16 bit</td><td>-32768 - 32767</td></tr>
<tr><td>int</td><td>32 bit</td><td>-2147483648 - 2147483647</td></tr>
<tr><td>long</td><td>64 bit</td><td>-huge - huge</td></tr>
<tr><td>float</td><td>32 bit</td><td>varies</td></tr>
<tr><td>double</td><td>64 bit</td><td>varies</td></tr>
</table>

# Declaration and initialization
- Instance variables get set to zero if not initialized after declaration 0, 0.0, false, null
- Local variables have to be initialized before usage or the program won't compile
# Comparison
- Primitive types: `==`
- Objects, to check if they refer to the same exact instance on the heap use == otherwise to check equality use `.equals()`
- 