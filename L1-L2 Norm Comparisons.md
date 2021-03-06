{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## L1 Norms versus L2 Norms\n",
    "\n",
    "<span style='color: gray'> <i>[2018/12/30: For my own lookup. This notebook is based on these two posts: __[kaggle notebook](https://www.kaggle.com/residentmario/l1-norms-versus-l2-norms)__ and __[Differences between L1 and L2 as Loss Function and Regularization](http://www.chioka.in/differences-between-l1-and-l2-as-loss-function-and-regularization/)__]</i></span>\n",
    "\n",
    "### Definition of Norms\n",
    "\n",
    "\"p-norm\" is defiend as: $$\\lVert x \\rVert_p = \\big(\\sum_i \\lvert x_i \\rvert^p\\big)^{1/p}$$\n",
    "\n",
    "L2-norm is 2-norm, which is also called Euclidian distance:\n",
    "$$\\lVert x \\rVert_2 = \\sqrt{\\big( \\sum_i x^2_i \\big)} = \\sqrt{x^2_1 + x^2_2 + \\dots + x^2_i}$$\n",
    "\n",
    "L1-norm is 1-norm, also known as Manhattan or taxicab distance:\n",
    "$$\\lVert x \\rVert_1 = \\sum_i \\lvert x_i\\rvert = \\lvert x_1\\rvert + \\lvert x_2\\rvert + \\dots + \\lvert x_i\\rvert$$\n",
    "\n",
    "### Loss Function\n",
    "L1-norm loss function is also known as least absolute deviations (errors). It is basically minimizing the _sum_ of the _absolute differences_ between the true value $Y_i$ and the estimated value $f(x_i)$.\n",
    "\n",
    "$$ L = \\sum_i \\lvert y_i - f(x_i) \\rvert $$\n",
    "\n",
    "L2-norm loss function is known as least squares error which is minimizing the _sum_ of the _square of the differences_ between the true value $Y_i$ and the estimated value $f(x_i)$\n",
    "\n",
    "$$ L = \\sum_i (y_i - f(x_i))^2 $$\n",
    "\n",
    "**Robustness: L1 > L2**\n",
    "\n",
    "Robustness is defined as resistance to outliers in a dataset. L2-norm is more sensitive to the outlies than L1-norm since it squares the error. So L1 may be a better choice where otliers may be safely and effectively ignored. If outliers should be considered in some cases, then L2-norm is better. \n",
    "\n",
    "**Stability: L1 < L2**\n",
    "\n",
    "Stability is resistance to small horizontal adjustment of a datum. L2-norm is more stable in small adjustment of a data point is because L2-norm is continuous. L1 has absolute value which makes it a non-differenciable piecewise funtion.\n",
    "\n",
    "From wikipedia:\n",
    "> The instability property of the method of least absolute deviations means that, for a small horizontal adjustment of a datum, the regression line may jump a large amount. The method has continuous solutions for some data configurations; however, by moving a datum a small amount, one could “jump past” a configuration which has multiple solutions that span a region. After passing this region of solutions, the least absolute deviations line has a slope that may differ greatly from that of the previous line. In contrast, the least squares solutions is stable in that, for any small adjustment of a data point, the regression line will always move only slightly; that is, the regression parameters are continuous functions of the data.\n",
    "\n",
    "** Solution uniqueness: L1 many, L2 only one**\n",
    "\n",
    "L2-norm is Euclidean distance which is the shortest path between two points. It only has one right answer. While L1 may have more than 1.\n",
    "\n",
    "### Regularization\n",
    "\n",
    "Regularization is a very important technique in machine learning to prevent overfitting by adding a regularization term. The regularization term should __only__ be added to the cost function during __training__.\n",
    "\n",
    "Ridge regression and Lasso regression are extensions for linear regression, i.e. regularized linear regressions.\n",
    "\n",
    "Ridge loss (L2 regularization): $$L = \\sum_i (Y_i - f(x_i))^2 + \\lambda \\sum_i\\beta^2$$\n",
    "\n",
    "Lasso loss (L1 regularization): $$L = \\sum_i (Y_i - f(x_i))^2 + \\lambda \\sum_i \\lvert \\beta \\rvert$$\n",
    "\n",
    "**Feature Selection: L1 has, L2 doesn't**\n",
    "\n",
    "Ridge regression (L2-norm) can't zero out coefficients. It enforces the $\\beta$ coefficients to be lower but it does not enforce them to be zero. Lasso regression (L1-norm) can actually set irrelevant coefficients to zero and you may end up with fewer features than you started with.\n",
    "\n",
    "**Sparsity: L1 > L2**\n",
    "\n",
    "The build-in feature selection property explains L1 is more sparse than L2.\n",
    "\n",
    "**Computational efficiency: L1 < L2** \n",
    "\n",
    "As is mentioned before, L1 is a non-differenciable piecewise function which has no analytical solution, but L2 is not. So L2 is more computationally efficient. It's worth noting that L1 havs the sparsity properties which allows it to be used along with sparse algorithms, which makes the calculation more efficient."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.6.1"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
