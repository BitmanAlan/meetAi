# meetAi
<!DOCTYPE html>
<html lang="zh">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>AI 岗位提效学习页面</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    /* Custom styles for building progress */
    .building-bar {
      transition: width 1s ease;
      background-color: #007BFF;
    }

    .building-svg {
      background-color: #e9ecef;
      border-radius: 5px;
      height: 30px;
    }
  </style>
</head>

<body class="bg-gray-100 text-gray-900">

  <div class="max-w-4xl mx-auto p-6 bg-white shadow-lg rounded-lg mt-8">

    <!-- AI 关键词库 -->
    <div class="section mb-12" id="keyword-section">
      <h2 class="text-2xl font-semibold mb-4">AI 关键词库</h2>
      <button class="button px-6 py-3 bg-blue-600 text-white rounded-md hover:bg-blue-500 transition"
        onclick="showKeyword()">随机关键词</button>
      <p id="keyword-description" class="mt-4 text-lg text-gray-700"></p>
    </div>

    <!-- AI 文章资源 -->
    <div class="section mb-12" id="article-section">
      <h2 class="text-2xl font-semibold mb-4">AI 最新文章</h2>
      <ul class="space-y-3">
        <li>
          <a href="https://example.com/article1" class="text-blue-600 hover:underline" target="_blank">文章1 - 企业AI应用</a>
        </li>
        <li>
          <a href="https://example.com/article2" class="text-blue-600 hover:underline" target="_blank">文章2 - AI与岗位效率提升</a>
        </li>
      </ul>
    </div>

    <!-- 知识趣味测试 -->
    <div class="section mb-12" id="test-section">
      <h2 class="text-2xl font-semibold mb-4">知识趣味测试</h2>
      <button class="button px-6 py-3 bg-blue-600 text-white rounded-md hover:bg-blue-500 transition"
        onclick="startTest()">开始测试</button>

      <div id="test-questions" class="mt-6 space-y-4" style="display:none;">
        <p class="text-lg">问题1: AI在岗位中的应用最为广泛的是？</p>
        <button class="button px-6 py-3 bg-blue-600 text-white rounded-md hover:bg-blue-500 transition"
          onclick="answerQuestion(1)">自动化</button>
        <button class="button px-6 py-3 bg-blue-600 text-white rounded-md hover:bg-blue-500 transition"
          onclick="answerQuestion(2)">数据分析</button>
      </div>

      <div id="test-result" class="mt-6 text-lg font-semibold text-green-500"></div>

      <!-- 建筑进度 -->
      <div id="building" class="mt-8">
        <h3 class="text-lg font-semibold mb-2">建造进度</h3>
        <div id="building-svg" class="building-svg">
          <div class="building-bar" id="building-progress" style="width: 0%"></div>
        </div>
      </div>
    </div>

  </div>

  <script>
    let buildingProgress = 0;

    // 关键词库功能
    function showKeyword() {
      const keywords = [
        { term: "世界模型", description: "一种全局性AI模型，通过多领域的结合提高决策准确性。", example: "例如，全球气候预测模型。" },
        { term: "生成对抗网络", description: "由生成器与判别器组成的AI模型，常用于生成图像和声音。", example: "例如，DeepFake视频。" }
      ];
      const randomKeyword = keywords[Math.floor(Math.random() * keywords.length)];
      document.getElementById("keyword-description").innerHTML = `<b>${randomKeyword.term}</b>: ${randomKeyword.description} <br> 示例: ${randomKeyword.example}`;
    }

    // 开始测试
    function startTest() {
      document.getElementById("test-questions").style.display = "block";
      document.getElementById("test-result").innerHTML = "";
    }

    // 回答问题
    function answerQuestion(answer) {
      if (answer === 1) {
        buildingProgress += 20; // 每答对一题，建筑进度增加20%
        document.getElementById("test-result").innerHTML = "回答正确！继续加油！";
      } else {
        document.getElementById("test-result").innerHTML = "回答错误，试试其他答案！";
      }

      // 动画更新建筑进度
      document.getElementById("building-progress").style.width = buildingProgress + "%";

      // 完成建筑
      if (buildingProgress >= 100) {
        document.getElementById("building").innerHTML += "<p class='text-green-500 font-bold mt-4'>恭喜！你已经完成了建筑！</p>";
      }
    }
  </script>

</body>

</html>
