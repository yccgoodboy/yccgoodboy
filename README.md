Home.html
<!DOCTYPE html>
<html>
<head>
    <title>设备管理</title>
    <style>
        table {
            border-collapse: collapse;
            width: 50%; /* 调整表格宽度为页面的一半 */
            margin-left: 0; /* 居中对齐表格 */
        }

        th, td {
            border: 1px solid black;
            padding: 8px;
        }

        th {
            background-color: #f2f2f2;
        }
    </style>
</head>
<body>
<h1>设备管理</h1>

<!-- 左侧导航 -->
<div class="sidebar">
    <ul>
        <li><a href="/addDevice">新增设备</a></li>
        <li><a href="/findAllDevice">查看设备</a></li>
        <li><a href="/addDeviceClass">新增设备分类</a></li>
        <li><a href="/findAllDeviceClass">查看设备分类</a></li>
    </ul>
</div>

<!-- 右侧表格 -->
<div class="content">
    <!-- 设备列表 -->
    <h2>设备列表</h2>
    <table>
        <thead>
        <tr>
            <th>设备编号</th>
            <th>设备分类编号</th>
            <th>设备名称</th>
            <th>设备价格</th>
            <th>操作</th> <!-- 添加操作列 -->
        </tr>
        </thead>
        <tbody>
        <% devices.forEach(function(device) { %>
        <tr>
            <td><%= device.DeviceID %></td>
            <td><%= device.DeviceClassID %></td>
            <td><%= device.DeviceName %></td>
            <td><%= device.DevicePrice %></td>
            <td>
                <!-- 删除按钮 -->
                <button onclick="confirmDelete('<%= device.DeviceID %>')">删除</button>
                <!-- 查看按钮 -->
                <button onclick="viewDevice('<%= device.DeviceID %>')">查看</button>
                <!-- 修改按钮 -->
                <button onclick="updateDevice('<%= device.DeviceID %>')">修改</button>
            </td>
        </tr>
        <% }); %>
        </tbody>
    </table>

    <script>
        function confirmDelete(devId) {
            if (confirm("确认删除该设备吗？")) {
                window.location.href = "/deleteDevice?devId=" + devId;
            }
        }

        function viewDevice(devId) {
            window.location.href = "/findDevice?devId=" + devId;
        }

        function updateDevice(devId) {
            window.location.href = "/updateDevice?devId=" + devId;
        }
    </script>


    <!-- 设备分类表 -->
    <h2>设备分类列表</h2>
    <table>
        <thead>
        <tr>
            <th>设备分类编号</th>
            <th>设备分类名称</th>
            <th>操作</th> <!-- 添加操作列 -->
        </tr>
        </thead>
        <tbody>
        <% deviceClasses.forEach(function(deviceClass) { %>
        <tr>
            <td><%= deviceClass.DeviceClassID %></td>
            <td><%= deviceClass.DeviceClassName %></td>
            <td>
                <!-- 删除按钮 -->
                <button onclick="confirmDelete('<%= deviceClass.DeviceClassID %>')">删除</button>
                <!-- 查看按钮 -->
                <button onclick="viewDeviceClass('<%= deviceClass.DeviceClassID %>')">查看</button>
                <!-- 修改按钮 -->
                <button onclick="updateDeviceClass('<%= deviceClass.DeviceClassID %>')">修改</button>
            </td>
        </tr>
        <% }); %>
        </tbody>
    </table>

    <script>
        function confirmDelete(devClassId) {
            if (confirm("确认删除该设备分类吗？")) {
                window.location.href = "/deleteDeviceClass?devClassId=" + devClassId;
            }
        }

        function viewDeviceClass(devClassId) {
            window.location.href = "/findDeviceClass?devClassId=" + devClassId;
        }

        function updateDeviceClass(devClassId) {
            window.location.href = "/updateDeviceClass?devClassId=" + devClassId;
        }
    </script>

</div>

</body>
</html>
