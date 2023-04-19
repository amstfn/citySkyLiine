Step 14
Now you have something that is resembling a building. You are ready to create your first variable. Variable declarations begin with two dashes (-) and are given a name and a value like this: --variable-name: value;. In the rule for the bb1 class, create a variable named --building-color1 and give it a value of #999.

Step 15
To use a variable, put the variable name in parentheses with var in front of them like this: var(--variable-name). Whatever value you gave the variable will be applied to whatever property you use it on.

Add the variable --building-color1 you created in the previous step as the value of the background-color property of the .bb1a class

Step 17
Change the value of your variable from #999 to #aa80ff and you can see how it gets applied everywhere you used the variable. This is the main advantage of using variables, being able to quickly change many values in your stylesheet by just changing the value of a variable

Step 21Passed
The buildings are too spaced out. Squeeze them together by adding two empty div elements to the top of the .background-buildings element, two more at the bottom of it, and one more in between .bb3 and .bb4. These will be added as evenly-spaced elements across the container, effectively moving the buildings closer to the center.

Step 23
That didn't work. You should add a fallback value to a variable by putting it as the second value of where you use the variable like this: var(--variable-name, fallback-value). The property will use the fallback value when there's a problem with the variable. Add a fallback value of green to the background-color of .bb2.

That didn't work, because the variables you declared in .bb1 do not cascade to the .bb2 and .bb3 sibling elements. That's just how CSS works. Because of this, variables are often declared in the :root selector. This is the highest level selector in CSS; putting your variables there will make them usable everywhere. Add the :root selector to the top of your stylesheet, and move all your variable declarations there.

You should optimize your code. Move the position and top properties and values from .foreground-buildings to .background-buildings. Then select both .background-buildings and .foreground-buildings there, effectively applying those styles to both of the elements. You can use a comma (,) to separate selectors like this: selector1, selector2.

Step 40
Gradients in CSS are a way to transition between colors across the distance of an element. They are applied to the background property and the syntax looks like this:

gradient-type(
  color1,
  color2
);
In the example, color1 is solid at the top, color2 is solid at the bottom, and in between it transitions evenly from one to the next. In .bb1a, add a background property below the background-color property. Set it as a gradient of type linear-gradient that uses --building-color1 as the first color and --window-color1 as the second.

Step 41
You want to add the same gradient to the next two sections. Instead of doing that, create a new class selector called bb1-window, and move the height and background properties and values from .bb1a to the new class selector.

Step 42
Add the new bb1-window class to the .bb1a, .bb1b, and .bb1c elements. This will apply the gradient to them.

Step 46
You can specify where you want a gradient transition to complete by adding it to the color like this:

gradient-type(
  color1,
  color2 20%,
  color3
);
Here, it will transition from color1 to color2 between 0% and 20% of the element and then transition to color3 for the rest. Add 80% to the --building-color1 color of the .bb1d gradient so you can see it in action.

step 47
Remove orange from the .bb1d gradient and change the 80% to 50%. This will make --building-color1 solid for the top half, and then transition to --window-color1 for the bottom half.

Step 51
Gradient transitions often gradually change from one color to another. You can make the change a solid line like this:

linear-gradient(
  var(--first-color) 0%,
  var(--first-color) 40%,
  var(--second-color) 40%,
  var(--second-color) 80%
);
Add a linear-gradient to .bb2b that uses --building-color2 from 0% to 6% and --window-color2 from 6% to 9%.

Step 52
You can see the hard color change at the top of the section. Change the gradient type from linear-gradient to repeating-linear-gradient for this section. This will make the four colors of your gradient repeat until it gets to the bottom of the element; giving you some stripes, and saving you from having to add a bunch of elements to create them.

Step 60
So far, all the gradients you created have gone from top to bottom, that's the default direction. You can specify another direction by adding it before your colors like this:

gradient-type(
  direction,
  color1,
  color2
);
Fill in .bb3 with a repeating-linear-gradient. Use 90deg for the direction, your building-color3 for the first two colors, and window-color3 at 15% for the third. When you don't specify a distance for a color, it will use the values that makes sense. In this case, the first two colors will default to 0% and 7.5% because it starts at 0%, and 7.5% is half of the 15%.

Step 78
You can add multiple gradients to an element by separating them with a comma (,) like this:

gradient1(
  colors
),
gradient2(
  colors
);
Add a repeating-linear-gradient to .fb1c below the one that's there; use your --building-color4 from 0% to 10% and --window-color4 from 10% and 90%. This will fill in behind the gradient you added last.

Step 79
You're going to use some more border tricks for the top section. Add a border-bottom with a value of 7vh solid var(--building-color4) to .fb1a. This will put a 7vh height border on the bottom. But since the element has zero size, it only shows up as a 2px wide line from the 1px border that is on all the elements.

Step 80
When you increase the size of the left and right borders, the border on the bottom will expand to be the width of the combined left and right border widths. Add 2vw solid transparent as the value of the border-left and border-right properties of .fb1a. They will be invisible, but it will make the border on the bottom 4vw wide.

Step 102Passed
The windows are stacked on top of each other on the rightmost purple building. Turn the building into a flexbox parent, and use the flex-wrap property to put the windows side by side, and push them down to a new row when they don't fit.

Step 113
At the top of the sky gradient color list, where you would put a direction for the gradient; add circle closest-corner at 15% 15%,. This will move the start of the gradient to 15% from the top and left. It will make it end at the closest-corner and it will maintain a circle shape. These are some keywords built into gradients to describe how it behaves.