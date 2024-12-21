# MetadataManager 使用说明

## 简介

`MetadataManager` 是一个简单的 JSON 元数据管理器，旨在方便地读取、写入和操作 JSON 文件。它提供了一系列方法来管理嵌套的 JSON 数据结构，支持添加、删除、读取和更新操作。

## 特性

- 读取和解析 JSON 文件
- 保存和更新 JSON 文件
- 支持嵌套键的访问
- 支持从列表中添加和删除元素
- 可选的唯一性检查以防止重复项

## 安装

确保您已安装 Python 3.x。将 `metadata_manager.py` 文件下载到您的项目目录中。

```bash
# 克隆或下载代码
git clone https://github.com/amumu2022/MetadataManager.git
cd https://github.com/amumu2022/MetadataManager.git
```

## 使用方法

### 初始化

首先，您需要创建一个 `MetadataManager` 实例。您可以指定缓存目录的名称，默认为 `cache_path`。

```python
from metadata_manager import MetadataManager

manager = MetadataManager(cache_dir='your_cache_directory')
```

### 读取数据

使用 `read` 方法读取 JSON 文件中的数据。您可以提供多个键以访问嵌套数据。

```python
data = manager.read('your_file_name', 'key1', 'key2')
```

如果未提供键，则返回整个字典。

### 添加或更新数据

使用 `add` 方法添加或更新指定嵌套键的值。

```python
manager.add('your_file_name', 'key1', 'key2', value='your_value')
```

### 删除数据

使用 `delete` 方法删除指定嵌套键的值。

```python
success = manager.delete('your_file_name', 'key1', 'key2')
```

### 向列表中添加元素

使用 `add_to_list` 方法向指定键的列表中添加元素。可以选择设置 `unique` 参数以防止添加重复项。

```python
manager.add_to_list('your_file_name', 'your_list_key', value='new_value', unique=True)
```

### 从列表中移除元素

使用 `remove_from_list` 方法从指定键的列表中移除元素。

```python
success = manager.remove_from_list('your_file_name', 'your_list_key', value='value_to_remove')
```

## 示例

以下是一个完整的示例，展示了如何使用 `MetadataManager`：

```python
from metadata_manager import MetadataManager

# 创建 MetadataManager 实例
manager = MetadataManager()

# 添加数据
manager.add('example', 'user', 'name', value='Alice')
manager.add('example', 'user', 'age', value=30)

# 读取数据
name = manager.read('example', 'user', 'name')
print(name)  # 输出: Alice

# 向列表中添加元素
manager.add_to_list('example', 'user', 'hobbies', value='reading')
manager.add_to_list('example', 'user', 'hobbies', value='traveling', unique=True)

# 从列表中移除元素
manager.remove_from_list('example', 'user', 'hobbies', value='reading')

# 删除数据
manager.delete('example', 'user', 'age')
```

## 注意事项

- 确保 JSON 文件的格式正确，以避免解析错误。
- 在进行删除和更新操作时，请确保提供的键路径是正确的。

## 许可证

本项目采用 MIT 许可证，详情请参阅 LICENSE 文件。

## 贡献

欢迎任何形式的贡献！请提交问题或拉取请求。

## 联系

如有任何问题或建议，请联系作者：XDTEAM。
