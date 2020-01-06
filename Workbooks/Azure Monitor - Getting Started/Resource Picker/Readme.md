# <a name="picking-a-set-of-resources-to-analyze-in-workbooks"></a>选取一组要在工作簿中分析的资源

有了 `Resource Picker` 模板，就可以着手通过订阅、资源组和资源参数来设置工作簿的输入上下文。 设置默认参数是为了选取虚拟机，但你可以对它进行配置，以选取任何类型的资源。 模板还有一个 ARG 查询控件，展示如何在分析中使用参数。

![映像](Full.png)

## <a name="setting-up-the-resource-type-to-pick"></a>设置要选取的资源类型

1. 在工作簿工具栏中单击“`Edit`”。
2. 现在可以在 `Subscriptions` 之前看到下拉列表 `Resource type`：

    ![映像](Parameter.png)
3. 展开下拉列表，选择要选取的资源类型。 这样会根据你的选择更新订阅、资源组和资源下拉列表。
4. 单击参数控件底部右侧的“`Edit`”按钮。
5. 在参数网格中，将 `Resources` 行的 `Display name` 列从“虚拟机”  更改为所选资源类型的易记名称（例如“存储帐户”） 
6. 单击工作簿工具栏中的“`Done Editing`”。

## <a name="selecting-more-or-less-than-10-resources-by-default"></a>默认选择 10 个左右的资源

1. 在工作簿工具栏中单击“`Edit`”。
2. 单击参数控件底部右侧的“`Edit`”按钮。
3. 在参数网格中，选择 `Resources` 所对应的行
4. 单击“`Edit`”（或铅笔）图标控件工具栏。
5. 在弹出的“`Edit Parameter`”窗格中，向下滚动到 `Azure Resource Graph Query` 编辑器。 会有一个如下所示的查询：
    ```sql
    Resources
    | where type in~({ResourceTypes})
    | extend resourceGroupId = strcat('/subscriptions/', subscriptionId, '/resourceGroups/', resourceGroup)
    | where resourceGroupId in~({ResourceGroups}) or '*' in~({ResourceGroups})
    | order by name asc
    | extend Rank = row_number()
    | project value = id, label = name, selected = Rank <= 10, group = resourceGroup
    ```
    用于资源选择的代码位于查询的最后一行：`selected = Rank <= 10`。 

6. 将值从 10 更改为其他值即可更改默认选择