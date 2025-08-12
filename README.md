# 🧠 Property Transfer Manager Tool (PTMTool) for Unreal Engine

A powerful and intuitive **Unreal Editor plugin** that enables fast and reliable copying of **properties**, **functions**, and **macros** between Blueprints. This tool significantly improves productivity in complex Blueprint-based projects.

![PTMTool UI](https://www.dropbox.com/scl/fi/ksi5p1nx5os8160pz3ueo/PropertyPicker.png?rlkey=hbg3cob0i2kbjvgs5w0735ntz&st=6gd7gwsm&raw=1)

---

## ✨ Features

- 🔁 Copy properties from one Blueprint to another
- 📌 Preserve variable values, including arrays and structs
- 🚫 Clash detection for conflicting names or types
- 📚 Supports macros and function graphs
- 🎨 UI-based selection with color-coded type indicators
- 🔍 Filter and inspect Blueprint properties easily
- 📁 Transfer variables to and from **User Defined Structs**

---

## 🚀 Getting Started

### 🧩 Installation

1. Place the `PTMTool` plugin folder inside your project’s `Plugins/` directory.
2. Regenerate project files and recompile (for C++ projects).
3. Launch the Unreal Editor.
4. Focus the Editor on the Map Editor window (not Blueprint windows).
54. Open `Tools > Property Copy...` or `Tools > Function Copy...` to access the tool.

> Compatible with **Unreal Engine 4.XX** and potentially **UE5 with minor adjustments**.


![Menu](https://www.dropbox.com/scl/fi/vknzi9nzz8smyeb1o0ye0/PTT_Menu.png?rlkey=d7sfxu55afj8esdcggdyotr01&st=ohfsy26s&raw=1)


---


## 🖥️ How to Use

1. Open the **Property Transfer Manager** window from the Unreal Editor.
2. Select your **Source** and **Target** Blueprints.
3. Use the property/function picker to select which elements to transfer.
4. Press `Apply` to complete the transfer.

### ✅ Supported Types
- `bool`, `int`, `byte`, `float`
- `FName`, `FText`, `FString`
- `FVector`, `FRotator`, `FTransform`, `FColor`
- `TArray<T>`,  `TMap<T>`, `TSet<T>`, for all of the above types
- Object Reference types

### ⚠️ Clash Detection
- Red highlighting indicates name/type mismatches between Source and Target.
- These fields will not be copied unless resolved.

---

## 🧬 API Overview (Developers)

Header: [`PTMTool.h`](./Source/PTMTool/Public/PTMTool.h)

### Core Classes
- `FPTM_PropertyInfo`
- `FFTM_FunctionInfo`
- `FPropertyTransferManager`

### Key Methods

```cpp
// Blueprint Selection
UObject* GetSelectedBlueprint();
UBlueprint* GetBlueprintFromObject(UObject*);

// Property Transfer
TArray<FPTM_PropertyInfo> CollectBlueprintPropertyInfo(UObject*); // works with UUserDefinedStruct
bool CopyBlueprintProperty(UObject* Source, UObject* Target, const FName &Variable); // Blueprint or struct

// Function/Macro Transfer
TArray<FFTM_FunctionInfo> CollectBlueprintFunctionInfo(UObject*);
bool CopyBlueprintFunction(UObject* Source, UObject* Target, const FName &Function);
