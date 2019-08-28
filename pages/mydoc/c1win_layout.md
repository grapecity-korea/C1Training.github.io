---
title: ComponentOne for Winforms | 탐색 및 레이아웃
keywords: ComponentOne, Winforms, 탐색, 레이아웃, search, layout
last_updated: Aug 08, 2019
summary: "ComponentOne for Winforms 가 제공하는 탐색 및 레이아웃 컨트롤을 소개합니다."
sidebar: mydoc_sidebar
permalink: c1win_layout.html
folder: mydoc
---


## C1 Menus and Toolbars로 메뉴와 툴바 만들기

본문은 ComponentOne Menus and Toolbars™ for WinForms 컨트롤을 사용하여 어떻게 툴 바와 멀티 레벨 메뉴 및 콘텍스트 메뉴를 일시 정지/유동하는지 설명합니다.

  

### 1. 주 메뉴와 콘텍스트 메뉴 만들기

C1MainMenu 컨트롤과 C1ContextMenu컨트롤은 네비게이션과 명령에 사용되는 멀티 레이어, 멀티 메뉴를 표시할 수 있습니다. 각 메뉴마다 모두 일련의 명령 링크를 포함하며 모두 단일한 공유명령에 링크됩니다.

도구상자로부터 C1MainMenu 컨트롤과 C1ContextMenu컨트롤을 창에 드래그합니다. 그리고 컨트롤을 CommandLinks 속성을 통해 code또는Editor로 각기 다른 명령 링크CommandLink를 추가해 줍니다. ComandLink.Command 속성을 사용하여 명령을 지정합니다. 구체적인 것은 아래의 코드를 참고하세요. :

```csharp
private C1.Win.C1Command.C1CommandMenu c1CommandMenu_File = new C1.Win.C1Command.C1CommandMenu();
this.c1CommandMenu_File.Text = "파일"; 

private C1.Win.C1Command.C1CommandLink c1CommandLink1 = new C1.Win.C1Command.C1CommandLink();
this.c1CommandLink1.Command = this.c1CommandMenu_File;

private C1.Win.C1Command.C1MainMenu c1MainMenu1 = new C1.Win.C1Command.C1MainMenu();
this.c1MainMenu1.CommandLinks.AddRange(new C1.Win.C1Command.C1CommandLink[] {this.c1CommandLink1,});
```

### 2. C1ToolBar와 C1CommandDock 만들기

C1CommandDock컨트롤을 창에 드래그하여 C1Toolbar를 일시 정지하거나 작동시킵니다. 그리고 C1ToolBar 컨트롤을 CommandDock에 드래그합니다. 이것은 툴바의 컨트롤을 표시합니다. 마치 C1MainMenu 컨트롤과 마찬가지로 일련의 명령 링크도 포함합니다. CommandDock은 각기 다른 여러 개의 Toolbar를 추가할 수 있습니다. 코드는 다음을 참고하세요. :

```csharp
this.c1CommandDock1.Controls.Add(this.c1ToolBar_Tools);
this.c1CommandDock1.Controls.Add(this.c1ToolBar_Format);
this.c1CommandDock1.Controls.Add(this.c1ToolBar_Edit);
this.c1CommandDock1.Controls.Add(this.c1ToolBar_File);
```

### 3. C1CommandHolder 만들기

C1CommandHolder 컨트롤을 창에 드래그합니다. 해당 컨트롤은 메뉴와 툴바의 모든 명령을 단일한 집합으로 저장할 수 있습니다. 모든 명령은 C1CommandHolder의 Click 이벤트를 시작시킬 수 있습니다. 또한 여러 개의 메뉴와 툴 바 사이에 공유명령을 허용합니다. MainMenu, Toolbar 등의 컨트롤을 추가 할 때, C1CommandHolder 모듈로 자동 관리하고 진행할 수 있습니다.  
C1CommandHolder에 Click 이벤트를 걸고 상응하는 명령을 클릭하면 Click이벤트가 일어납니다. 코드는 다음의 표시와 같습니다. :

```csharp
private void c1CommandHolder1_CommandClick(object sender, CommandClickEventArgs e)
{
	//c1command click event
	label1.Text = "실행 " + e.Command.Text + " 조작";
 }
```

본문의 Demo 소스코드는 다음과 같습니다. :

  
![](https://www.grapecity.co.kr/images/training/c1/tc_winforms2-2-1.png)
  

아래 링크를 통해 좀 더 자세한 사항을 확인해보실 수 있습니다.

[샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/C1ContextMenuToolbarOverview.zip)


## C1TileControl로 Window10스타일 시뮬레이션의 문서파일브라우징 응용

Window 10 양식의 시뮬레이션 레이아웃을 사용할 때, C1TileControl은 여러 가지 옵션을 제공하고 선택한 내용에 따라 대응형 인터페이스 배열을 완성합니다. 이렇게 하면 그룹에 따라 아이콘을 자동적으로 바둑판 배열을 하고 임의의 크기로 설정할 수 있습니다. 또한 인터페이스를 일시 정지, 중첩 또는 내포를 할 수도 있고 텍스트 요소 및 애니메이션도 설정 가능합니다.

본문에서는 C1TilleControld을 어떻게 사용하여 Window10 스타일을 가지는 문서파일 브라우징 응용프로그램을 만드는지 소개합니다.

  

### 1. 그룹을 바둑판 형식으로 배치

TileControl.Groups.Add를 통해 TileControl을 위한 각각 다른 그룹을 추가할 수 있습니다. Tile 바둑판 패치는 각기 다른 그룹 속에 두어 그룹 형식으로 표시합니다. 본문 Demo에서 각각 다른 유형의 그룹을 만듭니다. 코드는 다음과 같습니다. :

```csharp
Group GetDriveGroup(DriveType driveType)
        {
            string groupName = driveType.ToString();
            foreach (Group group in itemTiles.Groups)
            {
                if (group.Name == groupName)
                {
                    return group;
                }
            }
            Group newGroup = new Group();
            switch (driveType)
            {
                case DriveType.CDRom:
                    newGroup.Text = "CD/DVD";
                    break;
                case DriveType.Fixed:
                    newGroup.Text = " 로컬 드라이브 ";
                    break;
                case DriveType.Network:
                    newGroup.Text = " 네트워크 드라이브 ";
                    break;
                case DriveType.Ram:
                    newGroup.Text = " 램 디스크 ";
                    break;
                case DriveType.Removable:
                    newGroup.Text = " 삭제된 드라이브 ";
                    break;
                default:
                    newGroup.Text = " Misc ";
                    break;
            }
            itemTiles.Groups.Add(newGroup);
            newGroup.Name = groupName;
            return newGroup;
        }
```

### 2. 패치 만들기

첫 번째 방법에서 TileControl은 이미 그룹 나누기에 추가되었습니다. 여기에서 패치 만들기를 통해 각기 다른 Tile 패치를 상응하는 그룹에 넣어야 합니다. 수직이나 수평으로 중첩되도록 선택할 수 있습니다. 그리고 Tile.Image 속성을 통해 그림을 추가합니다. 구체적인 코드는 다음과 같습니다. :

```csharp
    DriveType dt = drive.DriveType;
    Group group = GetDriveGroup(dt);

    Tile tile = new Tile();
    switch (dt)
    {
        case DriveType.CDRom:
            tile.Image = Title_FileExplorer.Properties.Resources.mediaDrive;
            break;
        case DriveType.Fixed:
            tile.Image = Title_FileExplorer.Properties.Resources.hardDrive;
            break;
        case DriveType.Network:
            tile.Image = Title_FileExplorer.Properties.Resources.networkDrive;
            break;
        default:
            tile.Image = Title_FileExplorer.Properties.Resources.otherDrive;
            break;
    }
    tile.HorizontalSize = 3;
    group.Tiles.Add(tile);
```

### 3. 패치 템플릿 만들기

근본적으로 각 바둑판 패치를 개별적으로 설계할 필요가 없습니다. 하나 또는 여러 개의 바둑판 템플릿을 만들고 이 템플릿들을 fileGroup.Tiles.Add를 통해 Tile에 추가합니다. 마지막으로 이 템플릿들과 패치를 Tile.Template속성을 통해 서로 연결되도록 합니다. 패치는 템플릿에 문자열, 색상 및 그림 같은 데이터를 제공할 수 있습니다. 템플릿과 여러 개의 바둑판 패치는 서로 연결됩니다. 또는 각각의 바둑판 패치는 템플릿을 따릅니다. 구체적인 연결코드는 다음과 같습니다. :

마지막으로 본문 마지막의Demo를 사용하여 C1TilleControl로 아래 그림과 같이 Window8 스타일을 가지는 문서파일 브라우징 응용프로그램을 만듭니다. :

```csharp
private C1.Win.C1Tile.Template tempDrive = new C1.Win.C1Tile.Template();
private C1.Win.C1Tile.C1TileControl itemTiles = new C1.Win.C1Tile.C1TileControl();
this.itemTiles.Templates.Add(this.tempDrive);
this.itemTiles.BackColor = System.Drawing.Color.Gainsboro;
this.itemTiles.CellHeight = 70;
this.itemTiles.CellWidth = 70;
Tile tile = new Tile();
folderGroup.Tiles.Add(tile);
tile.Template = tempFolder;
```

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms2-3-1.png)

  

[샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/C1TileControl.zip)


## C1Themes를 WinForms 응용프로그램에 추가하기

본문은 C1Themes를 기존의 WinForms 응용프로그램에 어떻게 추가하는지 소개합니다. C1Themes는 전문적으로 설계된 테마가 25종 이상 내장되어 있습니다. 또한 사용자가 테마를 정의하여 응용 프로그램에 적용할 수도 있습니다. 본문은 주로 C1FlexGrid와 C1TrueDBGrid의 테마 설정을 소개합니다. 다음 방법에 따라 ComponentOne Studio for WinForms의 C1Report, C1Ribbon 및 기타 컨트롤에 C1Themes를 추가할 수 있습니다.

  

### 1. C1ThemeController 추가

먼저, 변경해야 하는 테마의 컨트롤을 응용프로그램에 추가합니다. 본문 Demo에서 먼저 도구상자의 C1FlexGrid와C1TrueDBGrid를 창에 드래그합니다. 또한 두 개의 컨트롤에 데이터 바인딩을 합니다. C1FlexGridDataSource에는 Employees 데이터리스트를 바인딩하고 C1TrueDBGrid에는 EmployeesOrders를 바인딩합니다. 데이터 바인딩 코드는 다음과 같습니다. :

```csharp
this.c1TrueDBGrid1.DataSource = this.employeesOrdersBindingSource;
this.c1FlexGrid1.DataSource = this.employeesBindingSource;
```

그리고 도구상자에서 C1ThemeController를 창에 드래그하면 다음과 같은 에디터가 팝 업 됩니다.

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms2-4-1.png)

C1FlexGrid、C1TrueDBGrid의 어느 창에 각기 다른 테마를 설정해주고 None을 감출 수 있습니다.

  

### 2. 모든Themes를 ComboBox에 추가

표준ComboBox를 창에 추가한 후 FormLoad 할 때, C1ThemController의 모든 사용 가능한 테마를 ComboBox의 드롭 다운 메뉴에 추가하여 사용 시 편리하게 선택하고 테마를 초기화로 설정할 수 있습니다. 코드는 다음과 같습니다. :

```csharp
// populate combobox with all available themes
this.comboBox1.Items.AddRange(C1.Win.C1Themes.C1ThemeController.GetThemes());
// set initial theme
comboBox1.SelectedIndex = 0;

```

### 3. 테마설정

ComboBox의 SelectedIndexChanged 이벤트를 설정은 드롭 다운 상자를 열고 상응하는 테마를 선택할 때, 해당 이벤트를 전용하여 창의 모든 컨트롤 테마를 변경합니다. 구체적인 코드는 다음과 같습니다. :

```csharp
private void comboBox1_SelectedIndexChanged(object sender, EventArgs e)
        {
            // Set theme on the theme controller:
            this.c1ThemeController1.Theme = this.comboBox1.SelectedItem.ToString();
            // ...and apply it to all themable controls (this will override any control-specific theme settings):
            Action setTheme = null;
            setTheme = (c) =>
            {
                if (C1.Win.C1Themes.C1ThemeController.IsObjectThemeable(c))
                    this.c1ThemeController1.SetTheme(c, this.c1ThemeController1.Theme);
                foreach (Control cc in c.Controls)
                    setTheme(cc);
            };
            setTheme(this);
        }
    }
```

먼저, 코드를 바탕으로 C1ThemeController에 ComboBox 드롭다운 메뉴에서 선택한 Theme를 설정해줍니다. 그리고 모든 창의 컨트롤에서 해당 Theme를 사용합니다. 실행 결과는 다음 그림과 같습니다. ComboBox의 드롭다운 메뉴에서 각각 다른 Theme를 선택하여 창의 C1FlexGrid와 C1TrueDBGrid설정할 수 있습니다.

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms2-4-2.png)

  

[샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/C1Theme1.zip)