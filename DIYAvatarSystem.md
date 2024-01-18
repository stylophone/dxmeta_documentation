# DIYAvatarSystem API

### 获取原始表格
```
DIYAvatarSystem.Instance.GetTable();
```
获取模型资源表格。

### 获取资源数据
```
DIYAvatarSystem.Instance.GetResDatasByCatalog(DIYCatalog catalog);
DIYAvatarSystem.Instance.GetResDatasByType(DIYType type);
```

### 获取所有可用分类
```
var catalogs = DIYAvatarSystem.Instance.GetCatalogs();
foreach (var catalog in catalogs)
{
    var displayName = catalog.DisplayName;  // 显示名称
    var type = catalog.Type;                // 类型
}
```

### 创建模型容器
```
GameObject go = DIYAvatarSystem.Instance.NewContainer();
```
返回基础模型容器，只带身体和基础uv贴图。

### 添加部件
```
SkinnedMeshRenderer smr = DIYAvatarSystem.Instance.AddPortion(GameObject container, DIYType type = DIYType.Hair);
```
向容器内添加模型部件，返回SkinnedMeshRenderer类型。

### 设置皮肤
```
DIYAvatarSystem.Instance.SetSkin(SkinnedMeshRenderer smr, int resourceId);
DIYAvatarSystem.Instance.SetSkin(SkinnedMeshRenderer skinnedMeshRenderer, Texture2D texture);
```
更换SkinnedMeshRenderer贴图。可以只传资源Id，会自己去查表取Texture。

完整用例：
```
GameObject go = DIYAvatarSystem.Instance.NewContainer();
SkinnedMeshRenderer hair = DIYAvatarSystem.Instance.AddPortion(go, DIYType.Hair);
DIYAvatarSystem.Instance.SetSkin(hair, Texture2D.white);
```
