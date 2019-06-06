codemirror代码高亮显示，在线运行anty例子，在线预览：https://scandalyang.github.io/CodeMirror-runCode-antv/

代码：
  <!-- 引入文件 -->
    <script src="./js/g2.min.js"></script>
    <script src="./js/data-set.min.js"></script>
    <script src="./js/jquery.min.js"></script>
    <script src="./js/codemirror-merged.min.js"></script>
    <script src="./js/xml.js"></script>
    <script src="./js/javascript.js"></script>
    <script>

    </script>
    <link rel="stylesheet"
        href="./js/codemirror-merged.min.css" />
    <style>
      <!-- dom -->
    <button class="btn btn-primary" onclick="runCode()">运行</button>

    <div class="all">
        <div class="block" id="c1"></div>
        <!-- 存放代码 -->
        <textarea id="script_once_code">
            </textarea>

    </div>

    <!--show运行动态code-->
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
         editor.setValue(`<script>
               if (!flag) {
                        chart.clear();
                    } else {
                        flag = false;
                    }
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
                    const dv = ds.createView().source(list[0].list);
                    const sty = 'month*count';
                    chart.source(dv);
                    chart.interval().position(sty).color('month');
                    chart.render();
                    </scri${str}pt>`)
            runCode();
