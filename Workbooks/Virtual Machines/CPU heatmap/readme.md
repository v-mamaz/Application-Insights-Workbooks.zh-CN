# <a name="cpu-heatmap"></a><span data-ttu-id="336f8-101">CPU 热度地图</span><span class="sxs-lookup"><span data-stu-id="336f8-101">CPU heatmap</span></span>

<span data-ttu-id="336f8-102">此工作簿是可视化虚拟机 CPU 利用率中热点的好方法。</span><span class="sxs-lookup"><span data-stu-id="336f8-102">This workbook is a good way to visualize hot spots in the CPU utilization of your virtual machines.</span></span>

![绘出 CPU 热度地图](cpu-heatmap.png)

## <a name="changing-the-cpu-threshold"></a><span data-ttu-id="336f8-104">更改 CPU 阈值</span><span class="sxs-lookup"><span data-stu-id="336f8-104">Changing the CPU threshold</span></span>
<span data-ttu-id="336f8-105">默认情况下，此工作簿突出显示平均 `Percentage CPU` 大于 75% 的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="336f8-105">By default, this workbook highlights virtual machines with average `Percentage CPU` greater than 75%.</span></span> <span data-ttu-id="336f8-106">如果希望提高或降低此阈值，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="336f8-106">If you wish for this threshold to be higher or lower, these are the steps for follow:</span></span>

1. <span data-ttu-id="336f8-107">单击工具栏中的 `Edit` 项。</span><span class="sxs-lookup"><span data-stu-id="336f8-107">Click the `Edit` item in the toolbar.</span></span>
2. <span data-ttu-id="336f8-108">单击配置单元控件右下角的 `↑ Edit` 按钮。</span><span class="sxs-lookup"><span data-stu-id="336f8-108">Click on the `↑ Edit` button to the bottom-right of the hive control.</span></span>
3. <span data-ttu-id="336f8-109">在 `Columns Available After Merge` 列表中，向下滚动并选择 `[Added column] - Cell Color` 项。</span><span class="sxs-lookup"><span data-stu-id="336f8-109">In the `Columns Available After Merge` list, scroll down and select the `[Added column] - Cell Color` item.</span></span>
4. <span data-ttu-id="336f8-110">单击配置单元控件工具栏中的 `Edit added item` 按钮。</span><span class="sxs-lookup"><span data-stu-id="336f8-110">Click on the `Edit added item` button in the hive controls toolbar.</span></span>
5. <span data-ttu-id="336f8-111">在打开的窗格中，单击显示 `Percentage CPU > 75 Result is E8976A` 的项上的 `Edit` 以查看弹出的设置</span><span class="sxs-lookup"><span data-stu-id="336f8-111">In the pane tha opens up, click `Edit` on the item that says `Percentage CPU > 75 Result is E8976A` to see a settings pop up</span></span>
    1. <span data-ttu-id="336f8-112">将 `Second operand` 字段设置为所需的阈值，例如 90。</span><span class="sxs-lookup"><span data-stu-id="336f8-112">Set the `Second operand` field to the threshold you want - say 90.</span></span>
        <span data-ttu-id="336f8-113">![绘出 CPU 热度地图](cpu-heatmap-column-settings.png)</span><span class="sxs-lookup"><span data-stu-id="336f8-113">![Image a CPU heatmap](cpu-heatmap-column-settings.png)</span></span>
    2. <span data-ttu-id="336f8-114">单击弹出窗口中的操作。</span><span class="sxs-lookup"><span data-stu-id="336f8-114">Click op in the popup.</span></span>
6. <span data-ttu-id="336f8-115">单击“保存并关闭”</span><span class="sxs-lookup"><span data-stu-id="336f8-115">Click 'Save and close'</span></span>
7. <span data-ttu-id="336f8-116">在工作簿工具栏中选择 `Done Editing`。</span><span class="sxs-lookup"><span data-stu-id="336f8-116">Choose `Done Editing` in the workbook toolbar.</span></span>
