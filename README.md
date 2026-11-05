# 酒店预订系统（软件工程课程）

多酒店在线预订系统的需求分析与软件设计材料，覆盖实验一（需求分析）与实验二（软件设计与建模）。项目甲方：符子建（241220165）。

本期范围：顾客查询与预订、酒店房型与逐日库存价格、订单确认/改订/取消、入住退房、统计与日志。不包含在线支付、第三方平台、会员积分、智能门锁、动态定价和具体房间号分配。

## 仓库结构（Git）

```
.
├── requirements.md          # 实验一：需求列表（REQ-001～REQ-025）
├── chat.txt                 # 实验一：访谈与 AI 辅助过程记录
└── docs/
    └── design/              # 实验二：设计与建模
        ├── UML/             # PlantUML 源码与 PNG
        ├── UI界面/          # 十二个界面原型
        └── process/         # 实验报告.md、AI使用记录.md、report.css
```

以下内容**不入库**（见 `.gitignore`）：`docs/design/实验报告.pdf`、`docs/design/process/作业描述.txt`、`docs/design/process/类图反馈意见.txt`，以及用于 cslab-cms 的 `deliverables/` 目录。

## 报告 PDF 生成（本地）

```bash
cd docs/design/process
pandoc 实验报告.md -o 实验报告.html --standalone --css=report.css
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
  --headless --disable-gpu --no-pdf-header-footer \
  --print-to-pdf=../实验报告.pdf \
  "file://$(pwd)/实验报告.html"
rm -f 实验报告.html
```

## cslab-cms 提交（仅本机打包，不在仓库内）

课程要求上传 `实验2_学号_姓名.zip`，包内目录为 `实验2_231220170_央金灵卓/`，且只含 `实验报告.pdf`、`UML/`、`UI界面/`。在仓库根目录执行（会写入已 gitignore 的 `deliverables/`，**不要** `git add`）：

```bash
ROOT="deliverables/实验2_231220170_央金灵卓"
rm -rf "$ROOT" deliverables/实验2_231220170_央金灵卓.zip
mkdir -p "$ROOT"
cp docs/design/实验报告.pdf "$ROOT/"
cp -R docs/design/UML docs/design/UI界面 "$ROOT/"
(cd deliverables && zip -r 实验2_231220170_央金灵卓.zip 实验2_231220170_央金灵卓)
```

将 `deliverables/实验2_231220170_央金灵卓.zip` 上传至 cslab-cms 即可。

Git 历史中 `lab2/` 路径下的 UML 提交记录仍保留；当前设计文件以 `docs/design/` 为准。
