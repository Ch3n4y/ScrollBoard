# ScrollBoard.js

ACM竞赛滚榜展示插件，基于JQuery、Bootstrap

展示页面：[Demo](https://qinshaoxuan.github.io/ScrollBoard.js/)

按一次回车（可自行指定）可进行一步，即更新一个队的一个未知结果


### V 1.0.0 (2016-07-02)

实现了基本的滚榜展示功能

## 使用方法

### example
```HTML
<head>
    <link rel="stylesheet" type="text/css" href="bootstrap/css/bootstrap.min.css">
    <link rel="stylesheet" type="text/css" href="css/scrollboard.css">
    <script type="text/javascript" src="js/jquery.min.js"></script>
    <script type="text/javascript" src="bootstrap/js/bootstrap.min.js"></script>
    <script type="text/javascript" src="js/scrollboard.js"></script>
</head>
 
<body>
    <script type="text/javascript">
    var board = new Board(
        8,
        new Array(4, 4, 4),
        StringToDate("2012-10-13 19:00:00"),
        StringToDate("2012-10-16 01:00:00")
    );
    board.showInitBoard();
    $('html').keydown(function(e) {
        if (e.keyCode == 13) {
            board.keydown();
        }
    });
    </script>
</body>
```

由于展示效果需要，请使用空页面

`new Board(problemCount, medalCounts, startTime, freezeBoardTime)`Borad类构造方法：参数依次为题目数、奖牌数数组（分别为金银铜）、比赛开始时间、比赛封榜时间

`Board.showInitBoard()`方法：展示封榜时榜的状态

`Board.keydown()`方法：滚榜时的一步操作，即更新一个队的一个未知结果

`StringToDate(s)` 方法："yyyy-mm-dd hh:mm:ss"格式字符串转Date对象

### 获取数据

JS文件中的`getSubmitList()`和`getTeamList()`方法分别为获取提交数据和获取队伍数据，请根据后台JSON数据格式自行修改，代码内有详细的注释说明

contest_log.php 为导出数据脚本。