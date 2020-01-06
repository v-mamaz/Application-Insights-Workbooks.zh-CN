# <a name="picking-a-set-of-resources-to-analyze-in-workbooks"></a><span data-ttu-id="f0780-101">选取一组要在工作簿中分析的资源</span><span class="sxs-lookup"><span data-stu-id="f0780-101">Picking a set of resources to analyze in workbooks</span></span>

<span data-ttu-id="f0780-102">有了 `Resource Picker` 模板，就可以着手通过订阅、资源组和资源参数来设置工作簿的输入上下文。</span><span class="sxs-lookup"><span data-stu-id="f0780-102">The `Resource Picker` template gets you started with subscription, resource group and resource parameters to set up the input context of your workbook.</span></span> <span data-ttu-id="f0780-103">设置默认参数是为了选取虚拟机，但你可以对它进行配置，以选取任何类型的资源。</span><span class="sxs-lookup"><span data-stu-id="f0780-103">The default parameters are set to pick virtual machines, but you can configure it to pick any type of resource.</span></span> <span data-ttu-id="f0780-104">模板还有一个 ARG 查询控件，展示如何在分析中使用参数。</span><span class="sxs-lookup"><span data-stu-id="f0780-104">The template also has a ARG query control that shows you how to use the parameters in your analyses.</span></span>

![映像](Full.png)

## <a name="setting-up-the-resource-type-to-pick"></a><span data-ttu-id="f0780-106">设置要选取的资源类型</span><span class="sxs-lookup"><span data-stu-id="f0780-106">Setting up the resource type to pick</span></span>

1. <span data-ttu-id="f0780-107">在工作簿工具栏中单击“`Edit`”。</span><span class="sxs-lookup"><span data-stu-id="f0780-107">Hit `Edit` on the workbook toolbar.</span></span>
2. <span data-ttu-id="f0780-108">现在可以在 `Subscriptions` 之前看到下拉列表 `Resource type`：</span><span class="sxs-lookup"><span data-stu-id="f0780-108">You will now be able to see a drop down `Resource type` before `Subscriptions`:</span></span>

    ![映像](Parameter.png)
3. <span data-ttu-id="f0780-110">展开下拉列表，选择要选取的资源类型。</span><span class="sxs-lookup"><span data-stu-id="f0780-110">Expand the drop down and select the resource types you want picked.</span></span> <span data-ttu-id="f0780-111">这样会根据你的选择更新订阅、资源组和资源下拉列表。</span><span class="sxs-lookup"><span data-stu-id="f0780-111">This will update the subscription, resource group and resources drop down to match your selection.</span></span>
4. <span data-ttu-id="f0780-112">单击参数控件底部右侧的“`Edit`”按钮。</span><span class="sxs-lookup"><span data-stu-id="f0780-112">Click the `Edit` button at the bottom right of the parameter control.</span></span>
5. <span data-ttu-id="f0780-113">在参数网格中，将 `Resources` 行的 `Display name` 列从“虚拟机”  更改为所选资源类型的易记名称（例如“存储帐户”） </span><span class="sxs-lookup"><span data-stu-id="f0780-113">In the parameters grid, for the row `Resources`, change the `Display name` column from _Virtual machines_ to friendly name of your selected resource type (e.g. _Storage Accounts_)</span></span>
6. <span data-ttu-id="f0780-114">单击工作簿工具栏中的“`Done Editing`”。</span><span class="sxs-lookup"><span data-stu-id="f0780-114">Click `Done Editing` in the workbooks toolbar.</span></span>

## <a name="selecting-more-or-less-than-10-resources-by-default"></a><span data-ttu-id="f0780-115">默认选择 10 个左右的资源</span><span class="sxs-lookup"><span data-stu-id="f0780-115">Selecting more or less than 10 resources by default</span></span>

1. <span data-ttu-id="f0780-116">在工作簿工具栏中单击“`Edit`”。</span><span class="sxs-lookup"><span data-stu-id="f0780-116">Hit `Edit` on the workbook toolbar.</span></span>
2. <span data-ttu-id="f0780-117">单击参数控件底部右侧的“`Edit`”按钮。</span><span class="sxs-lookup"><span data-stu-id="f0780-117">Click the `Edit` button at the bottom right of the parameter control.</span></span>
3. <span data-ttu-id="f0780-118">在参数网格中，选择 `Resources` 所对应的行</span><span class="sxs-lookup"><span data-stu-id="f0780-118">In the parameters grid, select the row for `Resources`</span></span>
4. <span data-ttu-id="f0780-119">单击“`Edit`”（或铅笔）图标控件工具栏。</span><span class="sxs-lookup"><span data-stu-id="f0780-119">Click on the `Edit` (or pencil) icon control toolbar.</span></span>
5. <span data-ttu-id="f0780-120">在弹出的“`Edit Parameter`”窗格中，向下滚动到 `Azure Resource Graph Query` 编辑器。</span><span class="sxs-lookup"><span data-stu-id="f0780-120">In the `Edit Parameter` pane that pops up, scroll down to the `Azure Resource Graph Query` editor.</span></span> <span data-ttu-id="f0780-121">会有一个如下所示的查询：</span><span class="sxs-lookup"><span data-stu-id="f0780-121">It should have a query that looks like this:</span></span>
    ```sql
    Resources
    | where type in~({ResourceTypes})
    | extend resourceGroupId = strcat('/subscriptions/', subscriptionId, '/resourceGroups/', resourceGroup)
    | where resourceGroupId in~({ResourceGroups}) or '*' in~({ResourceGroups})
    | order by name asc
    | extend Rank = row_number()
    | project value = id, label = name, selected = Rank <= 10, group = resourceGroup
    ```
    <span data-ttu-id="f0780-122">用于资源选择的代码位于查询的最后一行：`selected = Rank <= 10`。</span><span class="sxs-lookup"><span data-stu-id="f0780-122">The code for resource selection is in the last line of the query: `selected = Rank <= 10`.</span></span> 

6. <span data-ttu-id="f0780-123">将值从 10 更改为其他值即可更改默认选择</span><span class="sxs-lookup"><span data-stu-id="f0780-123">Change the value from 10 to a different one to change the default selection</span></span>