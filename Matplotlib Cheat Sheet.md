# Matplotlib Cheat Sheet

    import matplotlib.pyplot as plt
    %matplotlib inline
    plt.show()

## Functional way
*	plt.plot(x,y)
*	plt.xlabel('X Label')
*	plt.ylabel('Y Label')
*	plt.title('Title')

*	plt.subplot(2,3,1) #nrows, ncols, plot number (1 to ncol*nrow)
plt.plot(x,y,'r')
plt.subplot(2,2,2)
plt.plot(y,x,'b')
plt.subplot(2,2,3)
plt.plot(x,y,'r')
plt.subplot(2,2,4)
plt.plot(y,x,'b')

## Object-oriented Method
*	fig = plt.figure() #imaginary blank canvas
axes1 = fig.add_axes([0.1,0.1,0.8,0.8])
axes1.plot(x,y)
axes1.set_xlabel('X Label')
axes1.set_ylabel('Y Label')
axes1.set_title('Set Title')
axes2 = fig.add_axes([0.5,0,0.5,0.5])
*	fig,axes = plt.subplots(nrows=1, ncols=2)
axes[0].plot(x,y,'r')
axes[0].set_title('First Plot')
axes[1].plot(y,x,'g')
axes[1].set_title('Second Plot')
plt.tight_layout()
*	fig = plt.figure(figsize=(8,2),dpi=100)
ax = fig.add_axes([0,0,1,1])
ax.plot(x,y)
*	fig, axes = plt.subplots(nrows=2,ncols=1,figsize=(8,2))
axes[0].plot(x,y)
axes[1].plot(y,x)
plt.tight_layout()
*	ax.legend(loc=0) #0 = best

*	fig.savefig('my_pic.png', dpi=300)
*	fig = plt.figure()
ax = fig.add_axes([0,0,1,1])
ax.plot(x,y,color='#aa11aa',lw=2, alpha=0.5, ls='-.', marker='o', markersize=10,markerfacecolor='yellow',markeredgewidth=3,markeredgecolor='green')
  line styles: '-', '--', '-.', ':', 'None', ' ', '', 'solid', 'dashed', 'dashdot', 'dotted'

*	ax.set_xlim([0,5])
ax.set_ylim([0,5])
*	plt.scatter(x,y)
*	plt.hist(data)
*	plt.boxplot(data,vert=True,patch_artist=True);

## Advanced
*	axes[1].set_yscale("log")
*	ax.set_xticks([1, 2, 3, 4, 5])
ax.set_xticklabels([r'$\alpha$', r'$\beta$', r'$\gamma$', r'$\delta$', r'$\epsilon$'], fontsize=18)
yticks = [0, 50, 100, 150]
ax.set_yticks(yticks)
ax.set_yticklabels(["$%.1f$" % y for y in yticks], fontsize=18); # use LaTeX formatted labels

*	from matplotlib import ticker
formatter = ticker.ScalarFormatter(useMathText=True)
formatter.set_scientific(True)
formatter.set_powerlimits((-1,1))
ax.yaxis.set_major_formatter(formatter)

*	fig, axes = plt.subplots(1, 4, figsize=(12,3))
axes[0].scatter(xx, xx + 0.25*np.random.randn(len(xx)))
axes[0].set_title("scatter")
axes[1].step(n, n**2, lw=2)
axes[1].set_title("step")
axes[2].bar(n, n**2, align="center", width=0.5, alpha=0.5)
axes[2].set_title("bar")
axes[3].fill_between(x, x**2, x**3, color="green", alpha=0.5);
axes[3].set_title("fill_between");


*	ax.text(0.15, 0.2, r"$y=x^2$", fontsize=20, color="blue")
ax.text(0.65, 0.1, r"$y=x^3$", fontsize=20, color="green");

*	Axes can be added to a matplotlib Figure canvas manually using fig.add_axes or using a sub-figure layout manager such as subplots, subplot2grid, or gridspec:

*	fig = plt.figure()
ax1 = plt.subplot2grid((3,3), (0,0), colspan=3)
ax2 = plt.subplot2grid((3,3), (1,0), colspan=2)
ax3 = plt.subplot2grid((3,3), (1,2), rowspan=2)
ax4 = plt.subplot2grid((3,3), (2,0))
ax5 = plt.subplot2grid((3,3), (2,1))
fig.tight_layout()


*	fig = plt.figure()  
gs = gridspec.GridSpec(2, 3, height_ratios=[2,1], width_ratios=[1,2,1])
for g in gs:
    ax = fig.add_subplot(g)
fig.tight_layout()
