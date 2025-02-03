# slerp-curve-visualizer
A small webpage that visualizes curves for SLERP merges on MergeKit

Made with Gemini in about an hour of iteration. One HTML file, so it oughta run anywhere. The values in the text box can be pasted right into some square brackets in a MergeKit .yaml config.

# (Attempted) Explanation

SLERP stands for "spherical linear interpolation", and the easiest way I can describe the basic mathematical concept is this.
If you're walking along the surface of a sphere, the shortest distance between your start point and end point would go through the inside of the sphere. The path that actually describes the walk, though, would go over the surface of the sphere. The first case is linear interpolation (LERP), the second is spherical linear interpolation (SLERP.)
Why we use SLERP for model merging is beyond me; I think it's just less "spiky". The point is,

When you have two models A and B, MergeKit interpolates the values of each parameter between the magnitudes of A and B, weighted via SLERP with a factor of `t`. `t` closer to 0 gets you closer to A, and `t` closer to 1 gets you closer to B. SLERP allows you to specify a layerwise weight for each parameter, so that parameters belonging to different layers of a model are treated differently; but it lets you do this *without* having to specify a value *for every layer.* (I believe this is where SLERP actually comes into play; if the number of values of `t` aren't the same as the number of layers in the models, then it SLERPs between them to get a more representative curve? Again, IDK. It's not documented very well. We move.)

The point of all of this is that the array of values `t` that you specify in your config describes a "shape" of the models' influence on the end product. The idea behind *this utility* is to make this fact more visual, in an interactive way.

Look, just try it, alright?
