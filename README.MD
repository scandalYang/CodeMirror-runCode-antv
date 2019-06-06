codemirror代码高亮显示，在线运行anty例子
 <script src="https://gw.alipayobjects.com/os/lib/antv/g2/3.4.10/dist/g2.min.js"></script>
    <script src="https://gw.alipayobjects.com/os/antv/assets/f2/3.3.8/f2.min.js"></script>
    <script src="https://gw.alipayobjects.com/os/antv/pkg/_antv.data-set-0.10.1/dist/data-set.min.js"></script>
    <script src="http://libs.baidu.com/jquery/2.0.0/jquery.min.js"></script>
    <script src="https://gw.alipayobjects.com/os/antv/assets/lib/codemirror-5.29.0/codemirror-merged.min.js"></script>
    <script src="./js/xml.js"></script>
    <script src="./js/javascript.js"></script>
    <script>

    </script>
    <link rel="stylesheet"
        href="https://gw.alipayobjects.com/os/antv/assets/lib/codemirror-5.29.0/codemirror-merged.min.css" />
    <style>
    <body>
    <!-- 创建图表容器 -->
    <button class="change" data="1">柱形分开1</button>
    <button class="change" data="2">柱形分开2</button>
    <button class="change" data="3">柱形合并1</button>
    <button class="change" data="5">折线分开1</button>
    <button class="change" data="6">折线分开2</button>
    <button class="change" data="8">面积图</button>
    <button class="change" data="7">折线合并</button>
    <button class="change" data="9">饼图</button>
    <button class="change" data="4">柱形合并2</button>
    <button class="btn btn-primary" onclick="runCode()">运行</button>
    <p>柱形分开</p>

    <div class="all">
        <div class="block" id="c1"></div>
        <textarea id="script_once_code">

                 <script>
                    const list = [
                        {
                            name: 'a', list: [
                                { month: '2-6', count: 12 },
                                { month: '3-6', count: 22 },
                                { month: '4-6', count: 32 },
                                { month: '5-6', count: 2 },
                                { month: '6-6', count: 22 },
                                { month: '7-6', count: 32 },
                                { month: '8-6', count: 72 },
                            ],

                        },
                        {
                            name: 'b', list: [
                                { month: '2-6', count: 22 },
                                { month: '3-6', count: 12 },
                                { month: '4-6', count: 42 },
                                { month: '5-6', count: 5 },
                                { month: '6-6', count: 32 },
                                { month: '7-6', count: 32 },
                                { month: '8-6', count: 42 },
                            ]
                        }
                    ]
                    chart.clear();
                    const ds = new DataSet();
                    const dv = ds.createView().source(list[1].list);
                    const sty = 'month*count';
                    chart.source(dv);
                    chart.interval().position(sty).color('month')
                    chart.render();
                </script>
            </textarea>

    </div>

    <!--show为存放动态code-->
    <div class="show"></div>
    <script>
        var editor = CodeMirror.fromTextArea(document.getElementById("script_once_code"), {
            mode: "text/html",
            styleActiveLine: true,
            lineNumbers: true,
            lineWrapping: true
        });
        var flag = true;
        var chart = new G2.Chart({
            container: 'c1', // 指定图表容器 ID
            forceFit: true,
        });
        function runCode() {
            $(".show").html(editor.getValue());
        }
