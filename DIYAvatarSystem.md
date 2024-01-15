# DIYAvatarSystem API

### 获取表格
```
DIYAvatarSystem.Instance.GetTable();
```
获取模型资源表格。

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
DIYAvatarSystem.Instance.SetSkin(SkinnedMeshRenderer smr, int id);
DIYAvatarSystem.Instance.SetSkin(SkinnedMeshRenderer skinnedMeshRenderer, Texture2D texture);
```
更换SkinnedMeshRenderer贴图。

完整用例：
```
GameObject go = DIYAvatarSystem.Instance.NewContainer();
SkinnedMeshRenderer hair = DIYAvatarSystem.Instance.AddPortion(go, DIYType.Hair);
DIYAvatarSystem.Instance.SetSkin(hair, Texture2D.white);
```
