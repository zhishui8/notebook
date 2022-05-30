# Plotting_setting

## Start

```python
fig,ax = plt.subplots(nrows=1,ncols=1,figsize = self.figsize)
fig.canvas.manager.set_window_title(self.figname)
```

## Spines

```python
ax1.spines['bottom'].set_linewidth(2.5)
ax1.spines['left'].set_linewidth(2.5)
ax1.spines['right'].set_linewidth(2.5)
ax1.spines['top'].set_linewidth(2.5)

ax.spines['right'].set_visible(False)
ax.spines['top'].set_visible(False)
ax.spines['left'].set_visible(False)
ax.spines['bottom'].set_visible(False)
    
```

## Ticks

```python
ax.tick_params(axis='both'/'x', which='both', direction='in',width=2, length=6, labelsize='刻度值字体大小',color='w',pad='刻度线与刻度值之间的距离'，bottom, top, left, right : bool, 分别表示上下左右四边，是否显示刻度线，True为显示，
              labelbottom, labeltop, labelleft, labelright :bool, 分别表示上下左右四边，是否显示刻度值，True为显示，
              labelrotation : 刻度值逆时针旋转给定的度数，如20
              gridOn: bool ,是否添加网格线； grid_alpha:float网格线透明度 ； grid_color: 网格线颜色; grid_linewidth:float网格线宽度； 			  grid_linestyle: 网格线型)
ref https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.tick_params.html
    
font = {'family': 'Times New Roman',
        'style': 'normal',
        'weight': 'bold',
        'color': 'k',
        'size': 25,
       }
ax.set_yticklabels([],font)
ax.set_xticklabels([],font)
ax.yaxis.set_minor_locator
ax.yaxis.set_major_locator



```

## Save figure

```
plt.savefig('../figname.jpeg',dpi=1000,bbox_inches = 'tight')
```

## Plot

```python
ax.plot(NormMx, MagnitudeMPeriod, label='Measured EMG', color='#BC2626', lw=4.5, linestyle='--')
ax.set_title('Biceps Femoris', title_font, y=1.05, fontsize=35)
    font = {'family': 'Times New Roman',
            'style': 'normal',
            'weight': 'bold',
            'color': 'k',
            'size': 25,
            }
ax.set_xlabel('Gait Cycle',font)
ax.set_ylabel('Gait Cycle',font)
ax,legend()




```

![image-20220530233800454](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205302339101.png)



