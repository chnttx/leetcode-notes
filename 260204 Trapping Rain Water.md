https://leetcode.com/problems/trapping-rain-water/

first thoughts: how do you even come up with naive solution...

I think this is similar to the thinking behind container with most water, if left wall < right wall ->  right wall only has to care about the first taller wall left of it, all the walls smaller than it wouldn't add any water

-> so maybe a stack? we pop until we find something that's larger or stack is empty (meaning we couldn't find a leftward wall taller than it)

calculating water amount is still similar, shorter height x width

but also need to handle what's already been calculated in the smaller subcontainers i.e 2 1 0 0 2 3. Approach: 
1. when we pop from stack, keep the highest that's shorter than both walls?
2. chuck all of the blocks in array (but this doesnt handle)
