# zyt_validation_utils

[![PyPI Version](https://img.shields.io/pypi/v/zyt_validation_utils.svg)](https://pypi.org/project/zyt_validation_utils/)
[![License](https://img.shields.io/pypi/l/zyt_validation_utils.svg)](https://opensource.org/licenses/MIT)
[![Python Version](https://img.shields.io/pypi/pyversions/zyt_validation_utils.svg)](https://www.python.org/downloads/)

**zyt_validation_utils** 是一个用于数据、文件、目录和文本验证的 Python 工具包。它提供了多种实用的验证函数，帮助开发者快速完成常见的数据检查任务。

---

## 功能特性

### 数据验证：
- 检查输入的全部元素是否全部为指定类型。
- 检查列表或元组中的元素是否唯一。
- 检查输入的全部元素是否都为空。
- 检查输入的全部元素是否都为数值类型。
- 检查输入的全部元素是否都为为指定类型数值（如奇数、正整数等）。
- 检查输入的全部元素是否在指定范围内。
- 检查输入的全部元素是否为字典的有效键。

### 目录验证：
- 检查路径是否为目录。
- 检查目录是否为空。
- 检查目录是否包含子目录或非子目录文件。

### 文件验证： 
- 检查路径是否为文件。
- 检查文件是否为空文件。
- 检查文件类型（如音频、视频、图片、压缩文件、bin文件、打包后的软件等）。
- 检查图片文件是否完整。
- 检查文件是否加载完整。

### 文本验证：
- 检查文本是否全为中文、英文、数字或特殊字符。
- 检查文本中是否包含中文、英文、数字、特殊字符、空格或空格符。
- 检查文本中是否包含给定的字符或子字符串。
- 检查给定的文本是否为有效的邮箱、URL、IP地址（IPV4、IPV6）、MAC地址、日期、<br>
颜色数、颜色（十六进制格式、RGB格式、RGBA格式）、身份证、手机号、邮编等

---
## API 文档

### 数据验证

#### `data_check`
- **`is_type(target_type, *datas)`**: 检查所有提供的数据是否匹配指定类型。
- **`is_all_unique(data)`**: 验证列表或元组的所有元素是否唯一。
- **`is_empty(*datas)`**: 判断提供的数据是否为空。
- **`is_numeric(*datas)`**: 检查所有提供的数据是否为数字。
- **`is_designated_nums(num_type, *datas)`**: 验证所有数据是否为指定的数字类型。
- **`is_nums_in_range(range_str, must_int=False, *datas)`**: 确保所有数字都在指定范围内。
- **`is_valid_key(dictionary, *datas)`**: 确认所有数据是否为字典中的有效键。

### 目录验证

#### `dir_check`
- **`is_dir(path, raise_error=True)`**: 检查路径是否为目录。
- **`is_dir_empty(dir_path)`**: 判断目录是否为空。
- **`is_have_subdirectories(dir_path)`**: 检查目录是否包含子目录。
- **`is_have_non_subdirectory_files(dir_path)`**: 验证目录中是否包含非子目录的文件。

### 文件验证

#### `file_check`
- **`is_file(path, raise_error=True)`**: 检查路径是否为文件。
- **`is_empty_file(file_path)`**: 判断文件是否为空。
- **`is_image(file_path, speed="normal", raise_error=True)`**: 验证文件是否为图片。
- **`is_image_complete(image_path, speed="normal", raise_error=True)`**: 检查图片文件是否完整。
- **`is_video(file_path, speed="normal", raise_error=True)`**: 验证文件是否为视频。
- **`is_audio(file_path, speed="normal", raise_error=True)`**: 检查文件是否为音频文件。
- **`is_archive(file_path, speed="normal", raise_error=True)`**: 判断文件是否为压缩文件。
- **`is_bin(file_path, speed="normal", raise_error=True)`**：判断文件是否为.bin文件。
- **`is_current_file_frozen()`**: 检查当前文件是否为打包后的软件。
- **`is_file_load_complete(file_path, timeout=60, raise_error=True)`**: 验证文件是否在超时时间内完全加载。

### 文本验证

#### `text_check`
- **`is_have_chinese(text)`**: 检查文本是否包含中文字符。
- **`is_all_chinese(text)`**: 判断整个文本是否全部由中文字符组成。
- **`is_have_english(text)`**: 检查文本是否包含英文字母。
- **`is_all_english(text)`**: 判断整个文本是否全部由英文字母组成。
- **`is_have_digit(text)`**: 检查文本是否包含数字。
- **`is_all_digit(text)`**: 判断整个文本是否全部由数字组成。
- **`is_have_special_char(text)`**: 检查文本是否包含特殊字符。
- **`is_all_special_char(text)`**: 判断整个文本是否全部由特殊字符组成。
- **`is_have_normal_space(text)`**: 检查文本是否包含普通空格。
- **`is_have_any_space(text)`**: 判断文本是否包含任何类型的空格。
- **`is_have(text, check)`**: 检查文本是否包含指定的子字符串。
- **`is_email(text)`**: 验证文本是否为有效的电子邮件地址。
- **`is_url(text)`**: 检查文本是否为有效的URL。
- **`is_ipv4_address(text)`**: 判断文本是否为有效的IPv4地址。
- **`is_ipv6_address(text)`**: 判断文本是否为有效的IPv6地址。
- **`is_ip_address(text)`**: 检查文本是否为有效的IP地址（IPv4或IPv6）。
- **`is_mac_address(text)`**: 验证文本是否为有效的MAC地址。
- **`is_date(text, separator='-')`**: 检查文本是否为有效的日期。
- **`is_color_num(text)`**: 判断文本是否为有效的颜色编号。
- **`is_hex_color(text)`**: 验证文本是否为有效的十六进制颜色。
- **`is_rgb_color(text)`**: 检查文本是否为有效的RGB颜色。
- **`is_rgba_color(text)`**: 判断文本是否为有效的RGBA颜色。
- **`is_color(text)`**: 验证文本是否为有效的颜色表示。
- **`is_Chinese_id_card(text, allow_lower_x=False)`**: 检查文本是否为有效的中国身份证号码。
- **`is_Chinese_mobile_phone_number(text)`**: 判断文本是否为有效的中国手机号码。
- **`is_Chinese_postal_code(text)`**: 验证文本是否为有效的中国邮政编码。

---

## 安装

使用 `pip`  安装：

```bash 
pip install zyt-validation-utils 
```
---


## 贡献

欢迎贡献代码！

## 许可证

本项目基于 [MIT 许可证](LICENSE) 开源。

## 作者

- **ZhangYuetao** - 项目开发者
- 邮箱: zhang894171707@gmail.com
- GitHub: [https://github.com/VerySeriousMan](https://github.com/VerySeriousMan)

## 致谢

感谢所有为这个项目做出贡献的人！