# Workbench中直接调用ICEM CFD进行网格划分

自从ANSYS 12.0之后，ICEM CFD就从Workbench中被分离出去，作为一个独立的程序使用了。取而代之的是Meshing模块。

1. 在Meshing的属性节点菜单中右键点击Mesh，选择Insert > Method，插入方法。

   ![image-20210811113619018](F:\Typora pic\image-20210811113619018.png)

2. 选择需要划分网格的几何体，点击apply。此时Geometry显示为**1 Body**。

   ![image-20210811113836688](F:\Typora pic\image-20210811113836688.png)

3. 设置**Method**为**MultiZone**，如果不设置成这个的话，找不到进入ICEM CFD的入口。如果要划分四面体，可以在**Mapped Mesh Type**中选择其他类型。

   ![image-20210811114154955](F:\Typora pic\image-20210811114154955.png)

4. 设定Write ICEM CFD Files为**Interactive**，即交互式使用。使用此方法进入ICEM CFD后，会自动进行分块。如果不选择Interactive，虽然也能进入ICEM CFD，但是用户不能重新建立分块，只能采用软件自动生成的块。

   ![image-20210811114324794](F:\Typora pic\image-20210811114324794.png)

5. 回到Meshing的属性节点菜单，右键点击Mesh，选择**Generate Mesh**生成网格，Meshing会自动启动ICEM CFD。

6. 启动ICEM CFD后，软件会自动分块(VORFN)，很明显自动分成的块并不是我们想要的。我们可以将其删除掉然后重新创建块。

   

   ![image-20210811135512259](F:\Typora pic\image-20210811135512259.png)

7. 设置Parts。Part要手动选取，与几何的Part一致。点击下拉框的小三角，选择与上方的part名一致的那个。这一步尤其重要，否则你建好了块到了Meshing后会重复进入ICEM CFD。

8. 根据需要在ICEM CFD中进行网格划分。

9. 生成网格。在ICEM CFD的网格并非真实的网格，只是网格预览。我们可以通过菜单**File > Mesh > Load From Blocking**生成实体网格。这时会弹出**Mesh Already Exists**的提示，我们选择**Replace**。

10. 关闭ICEM CFD。这时会提示是否保存。一定要选Yes，选了Yes之后，Meshing中的Mesh会继续网格生成。



