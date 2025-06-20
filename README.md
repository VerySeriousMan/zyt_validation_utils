# zyt_validation_utils

[![PyPI Version](https://img.shields.io/pypi/v/zyt_validation_utils.svg)](https://pypi.org/project/zyt_validation_utils/)
[![License](https://img.shields.io/pypi/l/zyt_validation_utils.svg)](https://opensource.org/licenses/MIT)
[![Python Version](https://img.shields.io/pypi/pyversions/zyt_validation_utils.svg)](https://www.python.org/downloads/)

**zyt_validation_utils** 是一个用于数据、文件、目录和文本验证的 Python 工具包。它提供了多种实用的验证函数，帮助开发者快速完成常见的数据检查任务。

> 📌 当前版本：`v0.2.4` ｜ 🆕 [查看更新日志 »](#更新日志)

---

## 功能特性

### 数据验证：
- 检查输入的全部元素是否全部为指定类型。
- 检查列表或元组中的元素是否唯一。
- 检查输入的全部元素是否都为空。
- 检查输入的全部元素是否都为数值类型。
- 检查输入的全部元素是否都为可转为整数或数值类型。
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
- 检查图片是否为指定类型图像（彩色图、灰度图或深度图）。

### 文本验证：
- 检查文本是否全为中文、英文、数字或特殊字符。
- 检查文本中是否包含中文、英文、数字、特殊字符、空格或空格符。
- 检查文本中是否包含给定的字符或子字符串。
- 检查给定的文本是否为有效的邮箱、URL、IP地址（IPV4、IPV6）、MAC地址、日期、<br>
颜色数、颜色（十六进制格式、RGB格式、RGBA格式）、身份证、手机号、邮编等

---

## 安装

使用 `pip`  安装：

```bash 
pip install zyt-validation-utils 
```
---

# API 文档

---

### 数据验证

#### `data_check`

该模块提供了一系列用于验证数据类型、唯一性、范围及其他属性的函数。以下是各函数的详细说明：

---

#### **`is_type(target_type, *datas)`**
**功能**: 检查所有提供的数据是否匹配指定类型。

**参数**:
- `target_type` (type): 目标类型（如 `str`, `int`, `list` 等）。
- `*datas`: 不定数量的待检测数据。

**返回**:
- `bool`: 如果所有数据都属于目标类型，返回 `True`；否则返回 `False`。

---

#### **`is_all_unique(data)`**
**功能**: 验证列表或元组的所有元素是否唯一。

**参数**:
- `data` (list 或 tuple): 待检测的列表或元组。

**返回**:
- `bool`: 如果所有元素都唯一，返回 `True`；否则返回 `False`。

**异常**:
- `TypeError`: 如果输入不是列表或元组。

---

#### **`is_empty(*datas)`**
**功能**: 判断提供的数据是否为空。

**支持的空值类型**:
- `None`
- 空字符串 (`""`)
- 空列表 (`[]`)
- 空字典 (`{}`)
- 空元组 (`()`)
- 空集合 (`set()`)

**参数**:
- `*datas`: 不定数量的待检测数据。

**返回**:
- `bool`: 如果所有数据都为空，返回 `True`；否则返回 `False`。

---

#### **`is_numeric(*datas)`**
**功能**: 检查所有提供的数据是否为数字。

**参数**:
- `*datas`: 不定数量的待检测数据。

**返回**:
- `bool`: 如果所有数据都是数值类型（`int` 或 `float`），返回 `True`；否则返回 `False`。

---

#### **`is_can_to_int(*datas)`**
**功能**: 检测所有数据是否都可以转换为整数。

**参数**:
- `*datas`: 不定数量的待检测数据。

**返回**:
- `bool`: 如果所有数据都可以转换为整数，返回 `True`；否则返回 `False`。

---

#### **`is_can_to_numeric(*datas)`**
**功能**: 检测所有数据是否都可以转换为数值（整数或浮点数）。

**参数**:
- `*datas`: 不定数量的待检测数据。

**返回**:
- `bool`: 如果所有数据都可以转换为数值，返回 `True`；否则返回 `False`。

---

#### **`is_designated_nums(num_type, *datas, must_int=False)`**
**功能**: 验证所有数据是否为指定的数字类型。

**支持的指定类型**:
- `"odd"`: 奇数
- `"even"`: 偶数
- `"positive"`: 正数
- `"no_negative"`: 非负数
- `"negative"`: 负数
- `"no_positive"`: 非正数

**参数**:
- `num_type` (str): 指定的数字类型。
- `*datas`: 不定数量的待检测数据。
- `must_int` (bool, 可选): 是否必须为整数。默认为 `False`。

**返回**:
- `bool`: 如果所有数据都符合指定类型，返回 `True`；否则返回 `False`。

**异常**:
- `ValueError`: 如果指定类型不支持。

---

#### **`is_nums_in_range(range_str, *datas, must_int=False)`**
**功能**: 确保所有数字都在指定范围内。

**参数**:
- `range_str` (str): 数据范围字符串，格式为 `(a, b)`、`[a, b]`、`(a, ]`、`[a, )`、`(, b)`、`[, b]` 等。
- `*datas`: 不定数量的待检测数据。
- `must_int` (bool, 可选): 是否必须为整数。默认为 `False`。

**返回**:
- `bool`: 如果所有数据都在指定范围内，返回 `True`；否则返回 `False`。

**异常**:
- `ValueError`: 如果范围字符串格式错误或数据不是有效数字。

---

#### **`is_valid_key(dictionary, *datas)`**
**功能**: 确认所有数据是否为字典中的有效键。

**参数**:
- `dictionary` (dict): 目标字典。
- `*datas`: 不定数量的待检测数据。

**返回**:
- `bool`: 如果所有数据都是字典的有效键，返回 `True`；否则返回 `False`。

---

### 使用示例

```python
from zyt_validation_utils.data_check import is_type, is_all_unique, is_empty, is_numeric, is_designated_nums, is_nums_in_range, is_valid_key

# 检查数据类型
if is_type(int, 1, 2, 3):
    print("所有数据都是整数")

# 检查列表元素是否唯一
if is_all_unique([1, 2, 3, 4]):
    print("列表元素唯一")

# 检查数据是否为空
if is_empty("", [], {}):
    print("所有数据都为空")

# 检查数据是否为数字
if is_numeric(1, 2.5, 3):
    print("所有数据都是数字")

# 检查数据是否为指定类型（如正数）
if is_designated_nums("positive", 1, 2, 3):
    print("所有数据都是正数")

# 检查数据是否在指定范围内
if is_nums_in_range("[1, 10]", 2, 3, 4, must_int=True):
    print("所有数据都在范围内")

# 检查数据是否为字典的有效键
if is_valid_key({"a": 1, "b": 2}, "a", "b"):
    print("所有数据都是字典的有效键")
```

---

### 目录验证

#### `dir_check`

该模块提供了一系列用于验证目录是否存在、是否为空、是否包含子目录或文件等功能的函数。以下是各函数的详细说明：

---

#### **`is_dir(path, raise_error=True)`**
**功能**: 检查路径是否为目录。

**参数**:
- `path` (str): 目录路径。
- `raise_error` (bool, 可选): 如果为 `True`，当路径不存在或不是目录时抛出异常；如果为 `False`，则返回 `False`。默认为 `True`。

**返回**:
- `bool`: 如果路径是目录，返回 `True`；否则返回 `False`。

**异常**:
- `FileNotFoundError`: 如果路径不存在且 `raise_error` 为 `True`。

---

#### **`is_dir_empty(dir_path)`**
**功能**: 判断目录是否为空。

**参数**:
- `dir_path` (str): 目录路径。

**返回**:
- `bool`: 如果目录为空，返回 `True`；否则返回 `False`。

---

#### **`is_have_subdirectories(dir_path)`**
**功能**: 检查目录是否包含子目录。

**参数**:
- `dir_path` (str): 目录路径。

**返回**:
- `bool`: 如果目录包含子目录，返回 `True`；否则返回 `False`。

---

#### **`is_have_non_subdirectory_files(dir_path)`**
**功能**: 验证目录中是否包含非子目录的文件。

**参数**:
- `dir_path` (str): 目录路径。

**返回**:
- `bool`: 如果目录中包含非子目录的文件，返回 `True`；否则返回 `False`。

---

### 使用示例

```python
from zyt_validation_utils.dir_check import is_dir, is_dir_empty, is_have_subdirectories, is_have_non_subdirectory_files

# 检查路径是否为目录
if is_dir("/path/to/directory"):
    print("路径是目录")

# 检查目录是否为空
if is_dir_empty("/path/to/directory"):
    print("目录为空")

# 检查目录是否包含子目录
if is_have_subdirectories("/path/to/directory"):
    print("目录包含子目录")

# 检查目录中是否包含非子目录的文件
if is_have_non_subdirectory_files("/path/to/directory"):
    print("目录中包含非子目录的文件")
```

---

### 文件验证 
####`file_check`

该模块提供了一系列用于验证文件类型、完整性及其他属性的函数。以下是各函数的详细说明：

---

### **`is_file(path, raise_error=True)`**
**功能**: 检查指定路径是否为文件。

**参数**:
- `path` (str): 文件路径。
- `raise_error` (bool, 可选): 如果为 `True`，当路径不存在或不是文件时抛出异常；如果为 `False`，则返回 `False`。默认为 `True`。

**返回**:
- `bool`: 如果路径是文件，返回 `True`；否则返回 `False`。

**异常**:
- `FileNotFoundError`: 如果路径不存在且 `raise_error` 为 `True`。

---

### **`is_empty_file(file_path)`**
**功能**: 判断文件是否为空文件。

**参数**:
- `file_path` (str): 文件路径。

**返回**:
- `bool`: 如果文件大小为 0，返回 `True`；否则返回 `False`。

---

### **`is_image(file_path, speed="normal", raise_error=True)`**
**功能**: 验证文件是否为图片文件。

**参数**:
- `file_path` (str): 文件路径。
- `speed` (str, 可选): 检测模式，可选值为 `'fast'` 或 `'normal'`。默认为 `'normal'`。
  - `'fast'`: 仅通过文件后缀名快速判断。
  - `'normal'`: 使用 `filetype` 库进行更准确的判断。
- `raise_error` (bool, 可选): 如果为 `True`，当检测失败时抛出异常；如果为 `False`，则返回 `False`。默认为 `True`。

**返回**:
- `bool`: 如果文件是图片文件，返回 `True`；否则返回 `False`。

**异常**:
- `ValueError`: 如果检测失败且 `raise_error` 为 `True`。

---

### **`is_image_complete(image_path, speed="normal", raise_error=True)`**
**功能**: 检查图片文件是否完整。

**参数**:
- `image_path` (str): 文件路径。
- `speed` (str, 可选): 检测模式，可选值为 `'fast'`、`'normal'` 或 `'strict'`。默认为 `'normal'`。
  - `'fast'`: 仅检查文件大小和文件头。
  - `'normal'`: 检查文件大小、文件头和图像结构。
  - `'strict'`: 检查文件大小、文件头、图像结构和像素数据。
- `raise_error` (bool, 可选): 如果为 `True`，当检测失败时抛出异常；如果为 `False`，则返回 `False`。默认为 `True`。

**返回**:
- `bool`: 如果图片文件完整，返回 `True`；否则返回 `False`。

**异常**:
- `ValueError`: 如果检测失败且 `raise_error` 为 `True`。

---

### **`is_video(file_path, speed="normal", raise_error=True)`**
**功能**: 验证文件是否为视频文件。

**参数**:
- `file_path` (str): 文件路径。
- `speed` (str, 可选): 检测模式，可选值为 `'fast'` 或 `'normal'`。默认为 `'normal'`。
  - `'fast'`: 仅通过文件后缀名快速判断。
  - `'normal'`: 使用 `filetype` 库进行更准确的判断。
- `raise_error` (bool, 可选): 如果为 `True`，当检测失败时抛出异常；如果为 `False`，则返回 `False`。默认为 `True`。

**返回**:
- `bool`: 如果文件是视频文件，返回 `True`；否则返回 `False`。

**异常**:
- `ValueError`: 如果检测失败且 `raise_error` 为 `True`。

---

### **`is_audio(file_path, speed="normal", raise_error=True)`**
**功能**: 验证文件是否为音频文件。

**参数**:
- `file_path` (str): 文件路径。
- `speed` (str, 可选): 检测模式，可选值为 `'fast'` 或 `'normal'`。默认为 `'normal'`。
  - `'fast'`: 仅通过文件后缀名快速判断。
  - `'normal'`: 使用 `filetype` 库进行更准确的判断。
- `raise_error` (bool, 可选): 如果为 `True`，当检测失败时抛出异常；如果为 `False`，则返回 `False`。默认为 `True`。
  
**返回**:
- `bool`: 如果文件是音频文件，返回 `True`；否则返回 `False`。

**异常**:
- `ValueError`: 如果检测失败且 `raise_error` 为 `True`。

---

### **`is_archive(file_path, speed="normal", raise_error=True)`**
**功能**: 验证文件是否为压缩文件。

**参数**:
- `file_path` (str): 文件路径。
- `speed` (str, 可选): 检测模式，可选值为 `'fast'` 或 `'normal'`。默认为 `'normal'`。
  - `'fast'`: 仅通过文件后缀名快速判断。
  - `'normal'`: 使用 `filetype` 库进行更准确的判断。
- `raise_error` (bool, 可选): 如果为 `True`，当检测失败时抛出异常；如果为 `False`，则返回 `False`。默认为 `True`。

**返回**:
- `bool`: 如果文件是压缩文件，返回 `True`；否则返回 `False`。

**异常**:
- `ValueError`: 如果检测失败且 `raise_error` 为 `True`。

---

### **`is_bin(file_path, speed="normal", raise_error=True)`**
**功能**: 验证文件是否为二进制 `.bin` 文件。

**参数**:
- `file_path` (str): 文件路径。
- `speed` (str, 可选): 检测模式，可选值为 `'fast'` 或 `'normal'`。默认为 `'normal'`。
  - `'fast'`: 仅通过文件后缀名快速判断。
  - `'normal'`: 读取文件内容并检查是否包含二进制数据。
- `raise_error` (bool, 可选): 如果为 `True`，当检测失败时抛出异常；如果为 `False`，则返回 `False`。默认为 `True`。

**返回**:
- `bool`: 如果文件是二进制 `.bin` 文件，返回 `True`；否则返回 `False`。

**异常**:
- `ValueError`: 如果检测失败且 `raise_error` 为 `True`。

---

### **`is_current_file_frozen()`**
**功能**: 判断当前程序是否是打包后的可执行文件。

**返回**:
- `bool`: 如果当前程序是打包后的可执行文件，返回 `True`；否则返回 `False`。

---

### **`is_file_load_complete(file_path, timeout=60, raise_error=True)`**
**功能**: 检查文件是否在指定时间内完全加载（通常用于检测文件是否复制完成）。

**参数**:
- `file_path` (str): 文件路径。
- `timeout` (int, 可选): 最大等待时间（秒）。默认为 `60` 秒。
- `raise_error` (bool, 可选): 如果为 `True`，当文件不存在或不是文件时抛出异常；如果为 `False`，则返回 `False`。默认为 `True`。

**返回**:
- `bool`: 如果文件在超时时间内完全加载，返回 `True`；否则返回 `False`。

**异常**:
- `ValueError`: 如果文件不存在或不是文件且 `raise_error` 为 `True`。

---

### **`is_rgb_image(file_path, image_check_speed="normal", raise_error=True)`**
**功能**: 判断输入图像是否为彩色图像。

**参数**:
- `file_path` (str): 文件路径。
- `image_check_speed` 检测模式，继承自 is_image 的 `fast` 或 `normal`（默认）。
- `raise_error` (bool, 可选): 如果为 `True`，当输入不是图像或判断失败时抛出异常；如果为 `False`，则返回 `False`。默认为 `True`。

**返回**:
- `bool`: 如果文件是彩色图像，返回 `True`；否则返回 `False`。

**异常**:
- `ValueError`: 如果输入不是图像或判断失败且 `raise_error` 为 `True`。

---

### **`is_gray_image(file_path, image_check_speed="normal", raise_error=True)`**
**功能**: 判断输入图像是否为灰度图像。

**参数**:
- `file_path` (str): 文件路径。
- `image_check_speed` 检测模式，继承自 is_image 的 `fast` 或 `normal`（默认）。
- `raise_error` (bool, 可选): 如果为 `True`，当输入不是图像或判断失败时抛出异常；如果为 `False`，则返回 `False`。默认为 `True`。

**返回**:
- `bool`: 如果文件是灰度图像，返回 `True`；否则返回 `False`。

**异常**:
- `ValueError`: 如果输入不是图像或判断失败且 `raise_error` 为 `True`。

---

### **`is_depth_image(file_path, image_check_speed="normal", raise_error=True)`**
**功能**: 判断输入图像是否为深度图像。

**参数**:
- `file_path` (str): 文件路径。
- `image_check_speed` 检测模式，继承自 is_image 的 `fast` 或 `normal`（默认）。
- `raise_error` (bool, 可选): 如果为 `True`，当输入不是图像或判断失败时抛出异常；如果为 `False`，则返回 `False`。默认为 `True`。

**返回**:
- `bool`: 如果文件是深度图像，返回 `True`；否则返回 `False`。

**异常**:
- `ValueError`: 如果输入不是图像或判断失败且 `raise_error` 为 `True`。

---

### 使用示例

```python
from zyt_validation_utils.file_check import is_file, is_image, is_image_complete, is_file_load_complete

# 检查是否为文件
try:
    if is_file("path", raise_error=True):
        print("是文件格式")
    else:
        print("不是文件格式")
except FileNotFoundError:
    print(f"path不存在")

# 检查文件是否为图片
try:
    if is_file("example.jpg", raise_error=False):
        if is_image("example.jpg", speed="fast", raise_error=True):
            print("文件是图片")
        else:
            print("文件不是图片")
    else:
      print("不是文件或地址不存在")
except ValueError:
    raise 

# 检查图片文件是否完整
if is_image_complete("example.jpg", speed="strict", raise_error=False):
    print("图片文件完整")

if is_file_load_complete("example.jpg", timeout=120, raise_error=False):
    print("图片已加载完成")
```

---

### 文本验证

#### `text_check`

该模块提供了一系列用于验证文本内容、格式及其他属性的函数。以下是各函数的详细说明：

---

#### **`is_have_chinese(text)`**
**功能**: 判断字符串是否含有中文字符。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果字符串含有中文字符，返回 `True`；否则返回 `False`。

---

#### **`is_all_chinese(text)`**
**功能**: 判断字符串是否全部由中文字符组成。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果字符串全部由中文字符组成，返回 `True`；否则返回 `False`。

---

#### **`is_have_english(text)`**
**功能**: 判断字符串是否含有英文字符。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果字符串含有英文字符，返回 `True`；否则返回 `False`。

---

#### **`is_all_english(text)`**
**功能**: 判断字符串是否全部由英文字符组成。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果字符串全部由英文字符组成，返回 `True`；否则返回 `False`。

---

#### **`is_have_digit(text)`**
**功能**: 判断字符串是否含有数字。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果字符串含有数字，返回 `True`；否则返回 `False`。

---

#### **`is_all_digit(text)`**
**功能**: 判断字符串是否全部由数字组成。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果字符串全部由数字组成，返回 `True`；否则返回 `False`。

---

#### **`is_have_special_char(text)`**
**功能**: 判断字符串是否含有特殊字符（非字母、非数字、非中文）。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果字符串含有特殊字符，返回 `True`；否则返回 `False`。

---

#### **`is_all_special_char(text)`**
**功能**: 判断字符串是否全部由特殊字符组成（非字母、非数字、非中文）。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果字符串全部由特殊字符组成，返回 `True`；否则返回 `False`。

---

#### **`is_have_normal_space(text)`**
**功能**: 判断字符串是否含有空格字符。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果字符串含有空格字符，返回 `True`；否则返回 `False`。

---

#### **`is_have_any_space(text)`**
**功能**: 判断字符串是否含有空白字符（包括空格、制表符、换行符等）。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果字符串含有空白字符，返回 `True`；否则返回 `False`。

---

#### **`is_have(text, check)`**
**功能**: 判断字符串中是否包含给定的字符或子字符串。

**参数**:
- `text` (str): 输入的文本。
- `check`: 需要检查的字符、子字符串或判断函数。可以是单个字符、字符串、列表、集合或元组。

**返回**:
- `bool`: 如果包含给定的字符或子字符串，返回 `True`；否则返回 `False`。

---

#### **`is_email(text)`**
**功能**: 判断字符串是否为有效邮箱地址。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果是有效邮箱地址，返回 `True`；否则返回 `False`。

---

#### **`is_url(text)`**
**功能**: 判断字符串是否为有效 URL。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果是有效的 URL，返回 `True`；否则返回 `False`。

---

#### **`is_ipv4_address(text)`**
**功能**: 判断字符串是否为有效 IPv4 地址。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果是有效的 IPv4 地址，返回 `True`；否则返回 `False`。

---

#### **`is_ipv6_address(text)`**
**功能**: 判断字符串是否为有效 IPv6 地址。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果是有效的 IPv6 地址，返回 `True`；否则返回 `False`。

---

#### **`is_ip_address(text)`**
**功能**: 判断字符串是否为有效 IP 地址（支持 IPv4 和 IPv6）。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果是有效的 IP 地址，返回 `True`；否则返回 `False`。

---

#### **`is_mac_address(text)`**
**功能**: 判断字符串是否为有效 MAC 地址。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果是有效的 MAC 地址，返回 `True`；否则返回 `False`。

---

#### **`is_date(text, separator='-')`**
**功能**: 判断字符串是否为有效日期（支持多种分隔符）。

**参数**:
- `text` (str): 输入的文本。
- `separator` (str, 可选): 日期分隔符，默认为 `'-'`。

**返回**:
- `bool`: 如果是有效日期，返回 `True`；否则返回 `False`。

---

#### **`is_color_num(text)`**
**功能**: 判断输入是否为颜色编码数字（0-255）。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果是有效颜色编码数字，返回 `True`；否则返回 `False`。

---

#### **`is_hex_color(text)`**
**功能**: 判断输入是否为有效的十六进制颜色代码。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果是有效的十六进制颜色代码，返回 `True`；否则返回 `False`。

---

#### **`is_rgb_color(text)`**
**功能**: 判断输入是否为有效的 RGB 颜色格式。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果是有效的 RGB 颜色格式，返回 `True`；否则返回 `False`。

---

#### **`is_rgba_color(text)`**
**功能**: 判断输入是否为有效的 RGBA 颜色格式（支持透明度为 0-1 或 0-255）。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果是有效的 RGBA 颜色格式，返回 `True`；否则返回 `False`。

---

#### **`is_color(text)`**
**功能**: 判断输入是否为有效的颜色格式（支持十六进制、RGB、RGBA）。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果是有效的颜色格式，返回 `True`；否则返回 `False`。

---

#### **`is_Chinese_id_card(text, allow_lower_x=False)`**
**功能**: 判断字符串是否为有效中国身份证号。

**参数**:
- `text` (str): 输入的文本。
- `allow_lower_x` (bool, 可选): 是否允许小写 `x`，默认为 `False`。

**返回**:
- `bool`: 如果是有效身份证号，返回 `True`；否则返回 `False`。

---

#### **`is_Chinese_mobile_phone_number(text)`**
**功能**: 判断字符串是否为有效中国手机号。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果是有效手机号，返回 `True`；否则返回 `False`。

---

#### **`is_Chinese_postal_code(text)`**
**功能**: 判断字符串是否为有效中国邮政编码。

**参数**:
- `text` (str): 输入的文本。

**返回**:
- `bool`: 如果是有效邮政编码，返回 `True`；否则返回 `False`。

---

### 使用示例

```python
from zyt_validation_utils.text_check import is_have_chinese, is_have, is_email, is_ipv4_address, is_date, is_Chinese_id_card

# 检查字符串是否含有中文字符
if is_have_chinese("你好，世界"):
    print("字符串含有中文字符")

# 检查字符串是否满足所给条件
if is_have("spring is on the horizon", ["spring","summer", "autumn", "winter"]):
    print("字符串在所给条件中")

# 检查字符串是否为有效邮箱地址
if is_email("example@example.com"):
    print("字符串是有效邮箱地址")

# 检查字符串是否为有效 IPv4 地址
if is_ipv4_address("192.168.1.1"):
    print("字符串是有效 IPv4 地址")
    
# 检查字符串是否为有效日期
if is_date("2025.01.27", separator='.'):
    print("字符串是有效日期")

# 检查字符串是否为有效中国身份证号
if is_Chinese_id_card("11010519491231002x", allow_lower_x=True):
    print("字符串是有效中国身份证号")
```

---

## 更新日志

### V0.2.4

### 2025-03-03

### ✨ 新增功能

**1. `file_check`模块**  
- ① 新增检查图片是否为指定类型图像：
    - `is_rgb_image(file_path, image_check_speed="normal", raise_error=True)`：判断输入图像是否为彩色图
    - `is_gray_image(file_path, image_check_speed="normal", raise_error=True)`：判断输入图像是否为灰度图
    - `is_depth_image(file_path, image_check_speed="normal", raise_error=True)`：判断输入图像是否为深度图
    - `is_rgb_video(file_path, video_check_speed="normal", raise_error=True)`：判断输入图像是否为彩色图视频


### 📜 完整更新日志

 **点此查看所有历史版本和详细改动说明：**  
🔗[查看完整更新日志 »](CHANGELOG.md)

---

## 贡献

欢迎贡献代码！

## 许可证

本项目基于 [MIT 许可证](LICENSE) 开源。

## 作者

- **ZhangYuetao** - 项目开发者
- 邮箱: zhang894171707@gmail.com