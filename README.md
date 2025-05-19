# UnVoiceClone：面向生成式伪造语音欺骗的鲁棒主动防御系统

**项目简介：**  
随着语音伪造技术的飞速发展，金融欺诈、舆论引导等安全事件层出不穷。UnVoiceClone 致力于在音视频中预先添加鲁棒对抗扰动，破坏语音伪造模型的有效性，从源头遏制语音伪造行为，降低声纹信息被恶意利用的风险。

**项目主页：** https://setsu1na.github.io/VoiceSafety/  
**GitHub 仓库：** https://github.com/PeriodBLUE/VoiceSafety

## 项目内容

本项目包含以下文件和目录：

- `index.html` - 主页面，展示项目介绍和主要功能
- `style.css` - 样式文件
- `images/` - 存放项目相关图片资源
- `README.md` - 项目说明文档

## 主要特性

- **强抗克隆能力**：基于异性身份替换与 KL 散度声纹特征选择，显著提升防御后语音与原始语音的差异性，平均 PSD 值较现有方法提升 2.32–1.76。
- **高保真度**：引入高斯分布逼近损失与软约束损失，保证防御语音在语义与听感上的一致性，ASV 相似度提升至 84.73%。
- **鲁棒性强**：采用高斯噪声优化的 WaveGlow 对抗生成，确保防御效果在加噪、裁剪、AAC/MP3 压缩等操作后仍能保持 60.04% 防御成功率。
- **泛化性高**：动态加权集成多说话人编码器并融合梯度正则化 & SAM 技术，对未知黑盒模型（如 LVC-VC、VALL-E、XTTS2、ElevenLabs）平均防御成功率达 66.29%。
- **高效性**：借助 inaSpeechSegmenter 精准定位说话人片段并行多线程处理，系统处理时间平均缩短 20%。

## 系统架构

本系统采用 B/S 架构，分为三大模块：

1. **用户操作端（Front-end）**  
   - 基于 Flask 提供 Web 界面，支持音视频文件上传、原始/防御后文件在线播放。
2. **后台处理端（Back-end）**  
   - 集成核心防御算法：声纹隐私主动防御、WaveGlow 对抗生成、动态集成说话人编码器、梯度正则化优化等。
3. **结果输出端（Output）**  
   - 生成并导出防御后音视频，支持本地下载与二次转换测试。

## 核心算法

- **基于匿名异性身份替换的声纹隐私主动防御**：选择与原始声音 KL 散度最大之异性声纹，结合基音可控调节，强化防御后声纹区分度。
- **高斯扰动优化的 WaveGlow 对抗语音生成**：确保对抗扰动遵循高斯分布，提高压缩与噪声场景下的鲁棒性。
- **动态权重调整的集成说话人编码器策略**：对多模型损失进行历史统计归一化，动态分配攻击强度，提升对未知模型的泛化表现。
- **基于梯度正则化与锐度感知最小化 (SAM) 的扰动优化**：平衡模型整体平滑性与对抗扰动强度，增强防御稳定性。

## 项目模块与功能

- **前端**：HTML5, CSS3, JavaScript, Flask + Jinja2 模板 :contentReference[oaicite:22]{index=22}:contentReference[oaicite:23]{index=23}  
- **后端**：Python, Flask Web 框架 :contentReference[oaicite:24]{index=24}:contentReference[oaicite:25]{index=25}  
- **机器学习／语音处理**：PyTorch (WaveGlow), inaSpeechSegmenter, 多线程并行技术 :contentReference[oaicite:26]{index=26}:contentReference[oaicite:27]{index=27}  
- **多媒体处理**：FFmpeg (音视频提取与重组) :contentReference[oaicite:28]{index=28}:contentReference[oaicite:29]{index=29}  

## 如何使用

1. 打开 `index.html` 主页面
2. 浏览项目简介和主要功能
3. 通过导航菜单访问不同的功能模块
4. 按照界面提示进行音频/视频的上传和防御处理

## 未来规划

1. **增强用户界面交互体验**：优化页面布局和操作流程，提升用户友好性
2. **扩展防御模型支持**：增加对更多主流语音克隆与合成模型的防御能力
3. **性能优化**：提高音视频处理速度和防御强度
4. **多语言支持**：增加不同语言环境下的防御能力
5. **移动端适配**：开发移动应用版本，方便用户随时处理音视频文件

## 联系方式

- **Email**: unvoiceclone-team@gmail.com
- **GitHub Issues**: https://github.com/PeriodBLUE/VoiceSafety/issues

---

感谢您对 UnVoiceClone 项目的关注与支持！
