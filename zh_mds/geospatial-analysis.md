

[Elastic Docs](/guide/) ›[Elasticsearch Guide [8.9]](index.md)

[« Sum bucket aggregation](search-aggregations-pipeline-sum-bucket-
aggregation.md) [EQL search »](eql.md)

# 地理空间分析

您知道 Elasticsearch 具有地理空间功能吗？Elasticsearch和geo可以追溯到2010年。从那以后发生了很多事情，今天Elasticsearch提供了强大的地理空间功能和速度，所有这些都通过一个自动扩展的堆栈。

不确定从哪里开始使用 Elasticsearch 和 geo？然后，你来对地方了。

### 地理空间映射

Elasticsearch 支持两种类型的地理数据：geo_point支持纬度/纬度对的字段，andgeo_shape字段，支持点、线、圆、多边形、多多边形等。使用显式映射为地理数据字段编制索引。

有一个带有纬度/纬度对但没有geo_point映射的索引？使用运行时字段在不重新编制索引的情况下进行geo_pointfield。

###Ingest

数据通常是混乱和不完整的。通过引入管道，可以在编制索引之前清理、转换和扩充数据。

* 使用 GeoIP 添加 IPv4 或 IPv6 地址的地理位置。  * 使用地理网格处理器将网格图块或六边形单元格 ID 转换为描述其形状的边界框或多边形。  * 使用geo_match丰富反向地理编码的策略。例如，使用反向地理编码按 Web 流量可视化大都市区域。

###Query

地理查询回答位置驱动的问题。查找与查询几何图形相交、位于查询几何图形内、包含在查询几何图形中或不与查询几何图形相交的文档。将地理空间查询与全文搜索查询相结合，以获得无与伦比的搜索体验。例如，"向我展示居住在我们新健身房位置 5 英里范围内的所有订阅者，这些订阅者在去年加入并在他们的个人资料中提到了跑步"。

###Aggregate

聚合将您的数据汇总为指标、统计信息或其他分析。使用存储桶聚合根据字段值、范围或其他条件将文档分组到存储桶(也称为箱)中。然后，使用指标聚合根据每个存储桶中的字段值计算指标，例如总和或平均值。跨存储桶比较指标，从数据中获取见解。

地理空间存储桶聚合：

* 地理距离聚合评估每个geo_point位置与原点的距离，并根据范围确定其所属的存储桶(如果文档与原点之间的距离在存储桶的距离范围内，则文档属于存储桶)。  * Geohash 网格聚合将geo_point和geo_shape值分组到表示网格的存储桶中。  * Geohex 网格聚合将geo_point和geo_shape值分组到表示 H3 六边形单元格的存储桶中。  * Geotile 网格聚合将geo_point和geo_shape值分组到表示网格的存储桶中。每个单元格对应于许多在线地图站点使用的地图图块。

地理空间指标聚合：

* 地理边界聚合计算包含地理点或地理形状字段的所有值的地理边界框。  * 地理质心聚合根据地理字段的所有坐标值计算加权质心。  * 地理线聚合将存储桶中的所有geo_point值聚合到按所选排序字段排序的 LineString 中。使用geo_line聚合创建车辆轨迹。

组合聚合以执行复杂的地理空间分析。例如，要计算每个航班的最新 GPS 轨迹，请使用术语聚合将文档分组到每架飞机的存储桶中。然后使用地理线聚合来计算每架飞机的轨迹。在另一个示例中，使用地理切片网格聚合将文档分组到网格中。然后使用地理质心聚合查找每个网格像元的加权质心。

###Integrate

使用矢量切片搜索 API 在现有 GIS 基础设施中使用 Elasticsearch 地理数据。

###Visualize

使用 Kibana 可视化地理数据。将地图添加到仪表盘以从各个角度查看数据。

此仪表板显示了老山的影响。

!Kibana 仪表板显示 2021 年 8 月 31 日至 12 月 142021 日期间的别哈火山喷发情况

### 机器学习

让机器学习为你服务，并通过异常检测找到应该突出的数据。查找发生在异常位置的信用卡交易或具有异常源位置的 Web 请求。基于位置的异常检测可以轻松查找、探索异常并将其与其典型位置进行比较。

###Alerting

让您的位置数据通过地理警报推动见解和行动。通常称为地理围栏，在移动对象进入或离开边界时跟踪它们，以通过常见业务系统(电子邮件、Slack、Teams、PagerDuty 等)接收通知。

有兴趣了解更多吗？按照分步说明设置跟踪遏制警报以监控移动的车辆。

[« Sum bucket aggregation](search-aggregations-pipeline-sum-bucket-
aggregation.md) [EQL search »](eql.md)