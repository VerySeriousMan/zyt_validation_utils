# 更新日志

---

## V0.2.4

### 2025-03-03

### ✨ 新增功能

**1. `file_check`模块**  
- ① 新增检查图片是否为指定类型图像：
    - `is_rgb_image(file_path, image_check_speed="normal", raise_error=True)`：判断输入图像是否为彩色图
    - `is_gray_image(file_path, image_check_speed="normal", raise_error=True)`：判断输入图像是否为灰度图
    - `is_depth_image(file_path, image_check_speed="normal", raise_error=True)`：判断输入图像是否为深度图
    - `is_rgb_video(file_path, video_check_speed="normal", raise_error=True)`：判断输入图像是否为彩色图视频

---

## V0.2.3

### 2025-02-08

### ✨ 新增功能

**1. `data_check`模块**  
- ① 新增检查输入的全部元素是否都为可转为整数或数值类型：
    - `is_can_to_int(*datas)`：检测所有数据是否都可以转换为整数
    - `is_can_to_numeric(*datas)`：检测所有数据是否都可以转换为数值（整数或浮点数）

---

## V0.2.2

### 2025-01-27

### ⚙️ 功能优化

**1. `text_check`模块**  
- ① 优化`is_have(text, check)`函数，检查范围由单个字符、字符串、列表、集合或自定义函数改为单个字符、字符串、列表、集合或元组

---

## V0.2.0-V0.2.1

### 2025-01-24

### ✨ 新增功能

**1. `data_check`模块**  
- ① 新增检查输入的全部元素是否全部符合指定格式：
    - `is_empty(*datas)`：检查输入的全部元素是否都为空
    - `is_numeric(*datas)`：检查输入的全部元素是否都为数值类型
    - `is_designated_nums(num_type, *datas, must_int=False)`：检查输入的全部元素是否都为为指定类型数值（如奇数、正整数等）
    - `is_nums_in_range(range_str, *datas, must_int=False)`:检查输入的全部元素是否在指定范围内
    - `is_valid_key(dictionary, *datas)`：检查输入的全部元素是否为字典的有效键

**2. `file_check`模块**  
- ① 新增检查文件的完整性：
    - `is_image_complete(image_path, speed="normal", raise_error=True)`：检查图片文件是否完整
- ② 新增检查文件类型：
    - `is_current_file_frozen()`：判断当前程序是否是打包后的可执行文件

**3. `text_check`模块**  
- ① 新增检查文本中是否包含指定类型文本：
    - `is_have_normal_space(text)`：判断字符串是否含有空格字符
    - `is_have_any_space(text)`：判断字符串是否含有空白字符（包括空格、制表符、换行符等）
- ② 新增检查给定的文本是否为有效的指定格式类型：
    - `is_email(text)`：判断字符串是否为有效邮箱地址
    - `is_url(text)`：判断字符串是否为有效 URL
    - `is_ipv4_address(text)`：判断字符串是否为有效 IPv4 地址
    - `is_ipv6_address(text)`：判断字符串是否为有效 IPv6 地址
    - `is_ip_address(text)`：判断字符串是否为有效 IP 地址（支持 IPv4 和 IPv6）
    - `is_mac_address(text)`：判断字符串是否为有效 MAC 地址
    - `is_date(text, separator='-')`：判断字符串是否为有效日期（支持多种分隔符）
    - `is_color_num(text)`：判断输入是否为颜色编码数字（0-255）
    - `is_hex_color(text)`：判断输入是否为有效的十六进制颜色代码
    - `is_rgb_color(text)`：判断输入是否为有效的 RGB 颜色格式
    - `is_rgba_color(text)`：判断输入是否为有效的 RGBA 颜色格式（支持透明度为 0-1 或 0-255）
    - `is_color(text)`：判断输入是否为有效的颜色格式（支持十六进制、RGB、RGBA）
    - `is_Chinese_id_card(text, allow_lower_x=False)`：判断字符串是否为有效中国身份证号
    - `is_Chinese_mobile_phone_number(text)`：判断字符串是否为有效中国手机号
    - `is_Chinese_postal_code(text)`：判断字符串是否为有效中国邮政编码

### ⚙️ 功能优化

**1. 修复部分函数bug** 

---

## V0.1.0

### 2025-01-22

### 发布初版