Unisgned values are prone to overflowing since their end of range is 0 which is close to where the majority of numbers used are.
In c++ when comparing one signed and one unsigned integers the result is converted to unsigned which can be prone to bugs.