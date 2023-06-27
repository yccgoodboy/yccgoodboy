Home.html
<!DOCTYPE html>
<html>
<head>
    <title>首页</title>
    <style>
        .container {
            display: flex;
            width: 100%;
        }

        .sidebar {
            width: 20%;
            padding: 20px;
        }

        .content {
            width: 80%;
            padding: 20px;
        }

        table {
            border-collapse: collapse;
            width: 100%;
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
<div class="container">
    <div class="sidebar">
        <ul>
            <li><a href="/addDevice">新增设备</a></li>
            <li><a href="/findAllDevice">查看设备</a></li>
            <li><a href="/addDeviceClass">新增设备分类</a></li>
            <li><a href="/findAllDeviceClass">查看设备分类</a></li>
        </ul>
    </div>

    <!-- 右侧内容 -->
    <div class="content">
        <!-- 设备分类表 -->
        <h2>设备分类列表</h2>
        <table>
            <thead>
            <tr>
                <th>设备分类编号</th>
                <th>设备分类名称</th>
                <th>操作</th>
            </tr>
            </thead>
            <tbody>
            <!-- 使用服务器端模板引擎渲染设备分类数据 -->
            <% deviceClasses.forEach(function(deviceClass) { %>
            <tr>
                <td><%= deviceClass.DeviceClassID %></td>
                <td><%= deviceClass.DeviceClassName %></td>
                <td>
                    <!-- 删除按钮 -->
                    <button onclick="confirmDeleteClass('<%= deviceClass.DeviceClassID %>')">删除</button>
                    <!-- 查看按钮 -->
                    <button onclick="viewDeviceClass('<%= deviceClass.DeviceClassID %>')">查看</button>
                    <!-- 修改按钮 -->
                    <button onclick="updateDeviceClass('<%= deviceClass.DeviceClassID %>')">修改</button>
                </td>
            </tr>
            <% }); %>
            </tbody>
        </table>

        <!-- 设备列表 -->
        <h2>设备列表</h2>
        <table>
            <thead>
            <tr>
                <th>设备编号</th>
                <th>设备分类编号</th>
                <th>设备名称</th>
                <th>设备价格</th>
                <th>操作</th>
            </tr>
            </thead>
            <tbody>
            <!-- 使用服务器端模板引擎渲染设备数据 -->
            <% devices.forEach(function(device) { %>
            <tr>
                <td><%= device.DeviceID %></td>
                <td><%= device.DeviceClassID %></td>
                <td><%= device.DeviceName %></td>
                <td><%= device.DevicePrice %></td>
                <td>
                    <!-- 删除按钮 -->
                    <button onclick="confirmDeleteDevice('<%= device.DeviceID %>')">删除</button>
                    <!-- 查看按钮 -->
                    <button onclick="viewDevice('<%= device.DeviceID %>')">查看</button>
                    <!-- 修改按钮 -->
                    <button onclick="updateDevice('<%= device.DeviceID %>')">修改</button>
                </td>
            </tr>
            <% }); %>
            </tbody>
        </table>
    </div>
</div>

<script>
    function confirmDeleteClass(devClassId) {
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

    function confirmDeleteDevice(devId) {
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

</body>
</html>

