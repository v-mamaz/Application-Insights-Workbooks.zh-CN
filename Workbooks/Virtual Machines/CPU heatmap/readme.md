# <a name="cpu-heatmap"></a>CPU 热度地图

此工作簿是可视化虚拟机 CPU 利用率中热点的好方法。

![绘出 CPU 热度地图](cpu-heatmap.png)

## <a name="changing-the-cpu-threshold"></a>更改 CPU 阈值
默认情况下，此工作簿突出显示平均 `Percentage CPU` 大于 75% 的虚拟机。 如果希望提高或降低此阈值，请执行以下步骤：

1. 单击工具栏中的 `Edit` 项。
2. 单击配置单元控件右下角的 `↑ Edit` 按钮。
3. 在 `Columns Available After Merge` 列表中，向下滚动并选择 `[Added column] - Cell Color` 项。
4. 单击配置单元控件工具栏中的 `Edit added item` 按钮。
5. 在打开的窗格中，单击显示 `Percentage CPU > 75 Result is E8976A` 的项上的 `Edit` 以查看弹出的设置
    1. 将 `Second operand` 字段设置为所需的阈值，例如 90。
        ![绘出 CPU 热度地图](cpu-heatmap-column-settings.png)
    2. 单击弹出窗口中的操作。
6. 单击“保存并关闭”
7. 在工作簿工具栏中选择 `Done Editing`。
