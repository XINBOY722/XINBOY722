<!--
**konoXIN/konoXIN** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
# 你好，我是konoXIN 👋
## 一个兴趣使然的人

我喜欢编程，学习，创造，分享。我的目标是成为一个优秀的前端开发工程师。我的座右铭是：**文质彬彬，然后而君子**。

📄 [个人网站](https://www.konoxin.top/)  📮 cxhaoxs@outlook.com
    
👋 感谢你的来访，祝你生活编码两开花。

<div class="calendar" id="calendar"></div>
    <div class="legend">
        <div class="legend-item">
            <div class="legend-color" style="background: #ebedf0"></div>
            无数据
        </div>
        <div class="legend-item">
            <div class="legend-color" style="background: #9be9a8"></div>
            0-2小时
        </div>
        <div class="legend-item">
            <div class="legend-color" style="background: #40c463"></div>
            2-4小时
        </div>
        <div class="legend-item">
            <div class="legend-color" style="background: #30a14e"></div>
            4-6小时
        </div>
        <div class="legend-item">
            <div class="legend-color" style="background: #216e39"></div>
            6+小时
        </div>
    </div>
    <script>
        async function fetchData() {
            try {
                // 使用CORS代理
                const response = await fetch(
                    `https://wakatime.com/share/@konoXIN/6bc251ad-6994-4e2c-b3df-2352945ee104.json`
                );
                const data = await response.json();

                // 修正数据访问路径
                if (data) {
                    console.log("成功获取数据，天数:", data.days.length);
                    return data.days;
                } else {
                    console.warn("数据格式不符合预期:", data);
                    return [];
                }
            } catch (error) {
                console.error("获取数据失败:", error);
                return [];
            }
        }

        function getColor(hours) {
            if (!hours || hours === 0) return "#ebedf0"; // 无数据或0小时显示灰色
            if (hours < 2) return "#9be9a8"; // 0-2小时: 浅绿
            if (hours < 4) return "#40c463"; // 2-4小时: 中绿
            if (hours < 6) return "#30a14e"; // 4-6小时: 深绿
            return "#216e39"; // 6+小时: 最深绿
        }

        function renderCalendar(days) {
            const calendarEl = document.getElementById("calendar");
            const today = new Date();
            const startDate = new Date();
            startDate.setMonth(today.getMonth() - 11); // 显示最近12个月

            let currentDate = new Date(startDate);
            let currentMonth = currentDate.getMonth();

            // 添加月份标签
            // const monthLabel = document.createElement('div');
            // monthLabel.className = 'month-label';
            // monthLabel.textContent = currentDate.toLocaleString('zh-CN', { month: 'long' }) + ' ' + currentDate.getFullYear();
            // calendarEl.appendChild(monthLabel);

            // 跳过第一周的空白天数
            const firstDayOfWeek = currentDate.getDay();
            for (let i = 0; i < firstDayOfWeek; i++) {
                const emptyDay = document.createElement("div");
                emptyDay.className = "day";
                emptyDay.style.visibility = "hidden";
                calendarEl.appendChild(emptyDay);
            }

            while (currentDate <= today) {
                // 检查是否需要添加新的月份标签
                if (currentDate.getMonth() !== currentMonth) {
                    currentMonth = currentDate.getMonth();
                    // const monthLabel = document.createElement('div');
                    // monthLabel.className = 'month-label';
                    // monthLabel.textContent = currentDate.toLocaleString('zh-CN', { month: 'long' }) + ' ' + currentDate.getFullYear();
                    // calendarEl.appendChild(monthLabel);
                }

                const dateStr = currentDate.toISOString().split("T")[0];
                const dayData = days.find((d) => d.date === dateStr);
                const hours = dayData ? dayData.total / 3600 : 0; // 使用total字段计算小时数

                const dayEl = document.createElement("div");
                dayEl.className = "day";
                dayEl.style.backgroundColor = getColor(hours);
                dayEl.setAttribute("data-date", dateStr);
                dayEl.setAttribute("data-hours", hours.toFixed(1));

                calendarEl.appendChild(dayEl);

                currentDate.setDate(currentDate.getDate() + 1);
            }
        }

        (async function () {
            const data = await fetchData();
            renderCalendar(data);
        })();
    </script>
 <!--START_SECTION:waka-->
![Code Time](http://img.shields.io/badge/Code%20Time-2%2C208%20hrs%2058%20mins-blue)

![Profile Views](http://img.shields.io/badge/%E4%B8%AA%E4%BA%BA%E8%B5%84%E6%96%99%E8%A7%82%E7%9C%8B%E6%AC%A1%E6%95%B0-8-blue)

![Lines of code](https://img.shields.io/badge/%E4%BB%8E%E3%80%8CHello%20World%E3%80%8D%E8%B5%B7%E6%88%91%E5%B7%B2%E7%BB%8F%E5%86%99%E4%BA%86-318.2%20thousand%20%E8%A1%8C%E4%BB%A3%E7%A0%81-blue)

**我是早起的 🐤** 

```text
🌞 早晨                     219 commits         ████████░░░░░░░░░░░░░░░░░   30.98 % 
🌆 白天                     306 commits         ███████████░░░░░░░░░░░░░░   43.28 % 
🌃 傍晚                     167 commits         ██████░░░░░░░░░░░░░░░░░░░   23.62 % 
🌙 晚上                     15 commits          █░░░░░░░░░░░░░░░░░░░░░░░░   02.12 % 
```
📅 **我最有效率是在 星期一** 

```text
星期一                      162 commits         ██████░░░░░░░░░░░░░░░░░░░   22.91 % 
星期二                      120 commits         ████░░░░░░░░░░░░░░░░░░░░░   16.97 % 
星期三                      152 commits         █████░░░░░░░░░░░░░░░░░░░░   21.50 % 
星期四                      109 commits         ████░░░░░░░░░░░░░░░░░░░░░   15.42 % 
星期五                      104 commits         ████░░░░░░░░░░░░░░░░░░░░░   14.71 % 
星期六                      20 commits          █░░░░░░░░░░░░░░░░░░░░░░░░   02.83 % 
星期日                      40 commits          █░░░░░░░░░░░░░░░░░░░░░░░░   05.66 % 
```


📊 **本周消耗时间** 

```text
🕑︎ 时区: Asia/Shanghai

💬 编程语言: 
Vue.js                   18 hrs 25 mins      █████████████████░░░░░░░░   66.56 % 
Other                    3 hrs 48 mins       ███░░░░░░░░░░░░░░░░░░░░░░   13.77 % 
JavaScript               1 hr 58 mins        ██░░░░░░░░░░░░░░░░░░░░░░░   07.15 % 
HTML                     1 hr                █░░░░░░░░░░░░░░░░░░░░░░░░   03.66 % 
YAML                     47 mins             █░░░░░░░░░░░░░░░░░░░░░░░░   02.87 % 

🔥 编辑器: 
VS Code                  18 hrs 55 mins      █████████████████░░░░░░░░   68.37 % 
Trae                     5 hrs 4 mins        █████░░░░░░░░░░░░░░░░░░░░   18.36 % 
Edge                     3 hrs 40 mins       ███░░░░░░░░░░░░░░░░░░░░░░   13.27 % 

🐱‍💻 项目: 
AI_web                   16 hrs 56 mins      ███████████████░░░░░░░░░░   61.20 % 
hanisun-ilab-app         4 hrs 11 mins       ████░░░░░░░░░░░░░░░░░░░░░   15.13 % 
AI项目                     2 hrs 40 mins       ██░░░░░░░░░░░░░░░░░░░░░░░   09.69 % 
Laboratory_SET_Center    1 hr 4 mins         █░░░░░░░░░░░░░░░░░░░░░░░░   03.88 % 
xinBlog                  1 hr 3 mins         █░░░░░░░░░░░░░░░░░░░░░░░░   03.85 % 

💻 操作系统: 
Windows                  27 hrs 41 mins      █████████████████████████   100.00 % 
```

**我最常使用 HTML** 

```text
HTML                     9 repos             ███████████░░░░░░░░░░░░░░   42.86 % 
JavaScript               7 repos             ████████░░░░░░░░░░░░░░░░░   33.33 % 
Vue                      2 repos             ██░░░░░░░░░░░░░░░░░░░░░░░   09.52 % 
Stylus                   2 repos             ██░░░░░░░░░░░░░░░░░░░░░░░   09.52 % 
Less                     1 repo              █░░░░░░░░░░░░░░░░░░░░░░░░   04.76 % 
```




 Last Updated on 28/05/2025 21:43:37 UTC
<!--END_SECTION:waka-->
