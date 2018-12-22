# Thoery-of-CNNs

To first understand the CNN we must first understand what is convolution.
And before convolution we must understand what is an impulse and what is impulse response.

# Impulse function

Time Domain Description

One of the more useful functions in the study of linear systems is the "unit impulse function."   An ideal impulse function is a function that is zero everywhere but at the origin, where it is infinitely high.  However, the area of the impulse is finite.  This is, at first hard to visualize but we can do so by using the graphs shown below.

![alt_text](http://lpsa.swarthmore.edu/BackGround/ImpulseFunc/img2B.gif)

Consider first the ramp function shown in the upper left.  It is zero for t<0 and one for t>T, and goes linearly from 0 to 1 as time goes from 0 to T.  If we let T→0, we get a unit step function, γ(t) (upper right).  If we take the derivative of our ramp function (lower left), we get a rectangular pulse with height 1/T (the slope of the line) and width T.  This rectangular pulse has area (height·width) of one.  If we take the limit as T→0, we get a pulse of infinite height, zero width, but still with an area of one; this is the unit impulse and we represent it by δ(t).  Since we can't show the height of the impulse on our graph, we use the vertical axis to show the area.  The unit impulse has area=1, so that is the shown height.

Laplace Domain Description

The relationship between step function and impulse function is even more obvious in the Laplace Domain.  The definitions for both are given below.

Step Function 
![alt_text](http://lpsa.swarthmore.edu/BackGround/ImpulseFunc/imgD2.gif)

Impulse Function 
![alt_text](http://lpsa.swarthmore.edu/BackGround/ImpulseFunc/imgD4.gif)

Clearly from these definitions we have Δ(s)=s·Γ(s). Since multiplication by "s" in the Laplace Domain is equivalent to differentiation in time this tells us that the unit impulse function is simply the derivative of the unit step function.

Key Concept: The Impulse Function

The unit impulse function has zero width, infinite height and an integral (area) of one.  We plot it as an arrow with the height of the arrow showing the area of the impulse.

![alt_text](http://lpsa.swarthmore.edu/BackGround/ImpulseFunc/img7C.gif)

To show a scaled input on a graph, its area is shown on the vertical axis.  In the diagram below the area of the impulse function is "A."  For a scaled impulse (i.e., A·δ(t)), the multiplier in front of the impulse is the area.

![alt_text](http://lpsa.swarthmore.edu/BackGround/ImpulseFunc/img55.gif)

Aside: Other definitions of impulse

Note, there are other, equally valid, definitions of an impulse.  The only important result is that the function has width approaching zero, height approaching infinity and an area of one.  For example, consider a Gaussian curve.

![alt_text](http://lpsa.swarthmore.edu/BackGround/ImpulseFunc/img6F.gif)

It is well known that the area under this graph is always one one (ref).  The graph below shows the function for several values of  σ. 

![alt_text](http://lpsa.swarthmore.edu/BackGround/ImpulseFunc/img71.gif)

# Now undestanding what an impluse response is

The impulse response and frequency response are two attributes that are useful for characterizing linear time-invariant (LTI) systems. They provide two different ways of calculating what an LTI system's output will be for a given input signal. A continuous-time LTI system is usually illustrated like this:

![alt_text](https://i.stack.imgur.com/yzWBM.png)

n general, the system H maps its input signal x(t) to a corresponding output signal y(t). There are many types of LTI systems that can have apply very different transformations to the signals that pass through them. But, they all share two key characteristics:

The system is linear, so it obeys the principle of superposition. Stated simply, if you linearly combine two signals and input them to the system, the output is the same linear combination of what the outputs would have been had the signals been passed through individually. That is, if x1(t) maps to an output of y1(t) and x2(t) maps to an output of y2(t), then for all values of a1 and a2,

H{ a1x1(t) + a2x2(t) }= a1y1(t) + a2y2(t)

The system is time-invariant, so its characteristics do not change with time. If you add a delay to the input signal, then you simply add the same delay to the output. For an input signal x(t) that maps to an output signal y(t), then for all values of τ,

H{ x(t−τ) } = y(t−τ)

Discrete-time LTI systems have the same properties; the notation is different because of the discrete-versus-continuous difference, but they are a lot alike. These characteristics allow the operation of the system to be straightforwardly characterized using its impulse and frequency responses. They provide two perspectives on the system that can be used in different contexts.

Impulse Response:

The impulse that is referred to in the term impulse response is generally a short-duration time-domain signal. For continuous-time systems, this is the Dirac delta function δ(t), while for discrete-time systems, the Kronecker delta function δ[n] is typically used. A system's impulse response (often annotated as h(t) for continuous-time systems or h[n] for discrete-time systems) is defined as the output signal that results when an impulse is applied to the system input.

Why is this useful? It allows us to predict what the system's output will look like in the time domain. Remember the linearity and time-invariance properties mentioned above? If we can decompose the system's input signal into a sum of a bunch of components, then the output is equal to the sum of the system outputs for each of those components. What if we could decompose our input signal into a sum of scaled and time-shifted impulses? Then, the output would be equal to the sum of copies of the impulse response, scaled and time-shifted in the same way.

For discrete-time systems, this is possible, because you can write any signal x[n] as a sum of scaled and time-shifted Kronecker delta functions:

x[n] = ∑ x[k].δ[n−k]

Each term in the sum is an impulse scaled by the value of x[n] at that time instant. What would we get if we passed x[n] through an LTI system to yield y[n]? Simple: each scaled and time-delayed impulse that we put in yields a scaled and time-delayed copy of the impulse response at the output. That is:

y[n] = ∑ x[k].h[n−k]

where h[n] is the system's impulse response. The above equation is the convolution theorem for discrete-time LTI systems. That is, for any signal x[n] that is input to an LTI system, the system's output y[n] is equal to the discrete convolution of the input signal and the system's impulse response.

Now the question comes, why only the impluse function?
The answer is very simple. Because the magnitude of the impluse function is 1 it does not alter the magnitude of the input function so we get the actual output response from the system.

# Now moving on to the convolution

Refer this link:
https://www.analog.com/media/en/technical-documentation/dsp-book/dsp_book_Ch6.pdf
