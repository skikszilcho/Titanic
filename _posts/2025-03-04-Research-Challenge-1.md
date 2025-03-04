---
title: Research Challenge 1
published: true
---


[Research Challenge 2](https://skikszilcho.github.io/Titanic/Research-Challenge-2).


# [](#Challenge-1)Challenge 1

Trump, having recently introduced his Space Force 🚀, decides he wants to lay a space monitoring cable around the moon. The Democrats complain that it will damage the surface of the moon 🌕 and insist that the cable be raised 2m high to avoid destroying the moon’s ecosystem. Trump agrees but says that he will only allow it if the Democrats pay for the additional cable needed for his project thinking this will discourage them. If the cable costs an extra $450 per meter, how much will the Democrats have to pay to raise the cable?

## [](#Answer)Answer

Initially, some assumptions/understandings are established:

> The moon has a radius approximate to 1740 kilometers.
>The cable that the Space Force wants to lay will be layed around the entire circumference of the moon.
> The demand from the Democrats requires that the 2 meters be added to the initial radius used for the original cable requirement calculations
> Any additional cable required above the original required cable will cost $450 per meter
> The moon is spherical

Following the establishment of a common understanding, to solve the given problem, the circumference of the moon is calculated by $\( 2π(r_{moon})^2 = 2 * π * (1740 * 1000) = Circumference_{original} \)$. While the new circumference $\( Circumference_{New} \)$, after adjusting for the cable according to the demands of the Democrats, is calculated similarly to the original circumference with the $\( (1740 * 1000) \)$ being changed to $\( (1740 * 1000 + 2) \)$. This results in initially `10932742.43 meters` of cable required, however, following the demands of the Democrats, `10932755.0 meters` of cable would be required. Therefore $(\ Cost = 450(Circumference_{new} - Circumference_{original}) \)$, resulting in a cost of `$5656.5`. The `python` code is given below:

```python
# Calculation of extra cable to be payed for
print('Circumference = 2\N{GREEK SMALL LETTER PI}r\N{SUPERSCRIPT TWO}\n')
print('Therefore:')
circ_org = round(2 * np.pi * (1740 * 1000), 2)
circ_new = round(2 * np.pi * (1740 * 1000 + 2), 2)
extra_cable = round(circ_new - circ_org, 2)
extra_cost = round(450 * extra_cable, 2)
print(f'''Original Circumference (circ_org) = 2 * \u03C0 * (1740 * 1000) meters 
                                  = {circ_org} meters\n''')
print(f'''New Circumference (circ_new) = 2 * \u03C0 * (1740 * 1000 + 2) meters 
                                  = {circ_new} meters.\n''')
print(f'''The extra circumference required to ensure the cable is layed where the Democrats 
desire is {extra_cable} meters. The extra cost that will be incurred is ${extra_cost}.''')
```


![NASA Moon Image](https://www.nasa.gov/wp-content/uploads/2022/11/hls-eva-steps-apr2020_0_0-sq.jpg?resize=1024,1024)

