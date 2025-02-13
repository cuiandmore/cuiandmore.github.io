---
title: 旅行轨迹地图
date: 2025-2-13
layout: page
---

<script>
    // 动态显示当前日期
    var dateElement = document.getElementById('current-date');
    var currentDate = new Date().toLocaleDateString();
    dateElement.textContent = currentDate;
</script>

<div id="map" style="height: 500px; width: 70%; left: 15%"></div>

<script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
<link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />

<script>
    // 初始化地图
    var map = L.map('map').setView([39.9042, 116.4074], 5);

    // 添加地图图层
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: '© OpenStreetMap contributors'
    }).addTo(map);

    // 示例轨迹数据
    var flightPath = [
        [39.9042, 116.4074], // 北京
        [31.2304, 121.4737], // 上海
        [22.3964, 114.1095]  // 香港
    ];

    // 添加轨迹线
    L.polyline(flightPath, {color: 'blue'}).addTo(map);

    // 添加起点和终点标记
    L.marker(flightPath[0]).addTo(map).bindPopup('起点: 北京');
    L.marker(flightPath[flightPath.length - 1]).addTo(map).bindPopup('终点: 香港');
</script>