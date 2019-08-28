---
title: ComponentOne for Winforms | 리포트 생성과 문서 변환
keywords: ComponentOne, Winforms, 리포트, 문서, report, documentation
last_updated: Aug 08, 2019
summary: "ComponentOne for Winforms 가 제공하는 리포트 생성 및 문서 변환 컨트롤을 소개합니다."
sidebar: mydoc_sidebar
permalink: c1win_report.html
folder: mydoc
---


## C1Report：NorthWind데이터베이스를 사용하여 데이터를 표시

C1Report는 XML, Access, SQL Server, Oracle등을 포함하여 각종 데이터 소스 유형을 지원합니다. 이 밖에 Visual Studio .NET 데이터를 대상으로 IList, IList 및 IEnumerable 포트를 실현하기만 하면 C1Report가 지원됩니다.

본문은 C1Report가 바인딩한 데이터 소스를 시연합니다. NorthWind 데이터 베이스는 자주 볼 수 있는 보고서 양식을 표시하고 프린트합니다.

  

### C1Report데이터소스 바인딩

1. XML에서 설정하거나 얻은 사용자 데이터가 바인딩 된 데이터 소스를 가져옵니다. 예를 들어 NorthWind 데이터베이스에서이 문서 Demo XML 문서를 사용하여 데이터 소스를 구하는 코드는 다음과 같습니다. :

    ```csharp
    Provider=Microsoft.Jet.OLEDB.4.0;Data Source=|DataDirectory|C1Demo.mdb;Persist Security Info=FalseSELECT Categories.*, Products.* FROM Categories INNER JOIN Products ON Categories.CategoryID = Products.CategoryID;
    ```

2. 지정된 문자열에서 XML 문서를 로드합니다. XmlDocument 클래스는 XML 문서를 로드하고 메모리의 문서 트리 구조를 작성하는 .NET Framework 용 DOC 파서입니다. LoadXML을 통해 XML 문서를 로드하는 코드는 다음과 같습니다.

  

    ```csharp
    // add Description tab 
    desc = new Label(); 
    desc.Dock = DockStyle.Fill; 
    desc.BackColor = Color.White; 
    TabPage tabDesc = new TabPage("Description"); 
    tabDesc.Controls.Add(desc); 
    c1PrintPreviewControl1.PreviewNavigationPanel.Controls.Add(tabDesc); 
    doc = new XmlDocument(); 
    doc.LoadXml(Report_Load.Properties.Resources.Report); 
    comboReports.SelectedIndex = 0; 
    ```

### C1Report의 지정리포트 읽기

C1Report의 Load 방법을 통해 사용자는 읽을 보고서를 지정할 수 있습니다. 코드는 다음과 같습니다. :

```csharp
// load C1Report with selected report
c1Report1.Load(doc, reportName);
c1Report1.Sections.Header.Visible = false;
```

### C1Report미리 보기 프린트

코드만 있으면 C1Report를 지정하여 미리 보기한 보고서를 프린트할 수 있습니다. 코드는 다음과 같습니다. :

  

```csharp
// assign report to print preview control
c1PrintPreviewControl1.Document = c1Report1.Document;
```

이렇게 C1리포트는 NorthWind데이터 베이스를 사용하여 쉽게 데이터를 표시할 수 있습니다. 결과는 아래 그림과 같습니다. :

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms5-1-1.png)

  

본문 Demo의 소스코드는 다음과 같습니다. :

  

[샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/C1Report.zip)


## C1을 사용한 응용프로그램과 Excel소프트웨어의 호환 방법

본문에서는 C1을 사용하여 Excel소프트웨어와 호환하는 방법을 소개합니다.

Microsoft Excel을 설치할 필요 없이C1의 간단한 명령으로 작업노트, 작업 테이블을 불러올 수 있습니다. 그리고, 작업노트를 Excel파일로 저장합니다. C1XLBook의 과정을 사용하는 대상은 코드에서 파악한 Excel파일입니다. 어떤 데이터라도 응용하여 Excel로 전환할 수 있습니다. OpenXML양식은 더 작거나 압축된 XLSX파일을 지원하고 저장합니다.

본문의 Demo에서는 C1XLBook로 Excel을 가져와 C1Chart의 데이터 소스로 만듭니다. 실행 시, 왼쪽 패널에서 각기 다른 Excel파일을 선택하여 C1XLBook에 들여보내 데이터를 읽어오도록 합니다. 결과는 다음과 같습니다. :

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms5-2-1.png)

  

위의 기능을 실현하고자 한다면 Excel로부터 데이터를 읽어와야 합니다. 다음과 같은 방법으로 실행 가능합니다.

먼저, 도구상자에서 C1XLBook을 드래그하거나 만듭니다. C1XLBook에서 Excel 작업노트를 로딩하거나 만듭니다.

```csharp
C1XLBook _xlBook = new C1XLBook();

_xlBook.Load(AppDomain.CurrentDomain.BaseDirectory+ filename);
```

이어서, C1XLBook에 Excel을 로딩하면 작업테이블의 데이터를 엑세스 할 수 있습니다. 이 데이터들은 행, 열 및 유닛 셀로 구성된 간단한 시트입니다. 본문 Demo에서 필요한 데이터는 네 개입니다. : 전도, 압력, 온도, ph, 조작 유닛 셀이 얻은 데이터의 코드는 다음과 같습니다. :

  

```csharp
DrillDataPoints GetChartData(C1XLBook book)
    {
        // Get first sheet
        var sheet = book.Sheets[0];

        // Get location, date, and cell count
        var location = sheet[1, 1].Value as string;
        var date = (DateTime)sheet[2, 1].Value;
        var count = sheet.Rows.Count - 5;
        label.Text = string.Format("{0}, {1} points", location, count);

        // Get values into arrays for charting
        var drillData = new DrillDataPoints(count);
        for (int r = 0; r < count; r++)
        {
            drillData.Temperature[r] = (double)sheet[r + 5, 1].Value;
            drillData.Pressure[r] = (double)sheet[r + 5, 2].Value;
            drillData.Conductivity[r] = (double)sheet[r + 5, 3].Value;
            drillData.Ph[r] = (double)sheet[r + 5, 4].Value;
            drillData.Depth[r] = r;
        }
        drillData.ScaleValues();

        // Send data to chart
        return drillData;
    }
```

XLS 파일이나 XLSX파일을 내보낼 수도 있습니다. C1XLBook을 사용하여 Excel 버전과 호환되는 보고서를 생성 할 수 있는 C1Chart 컨트롤입니다.

내보내기 방법은 다음과 같습니다. ：

```csharp
//   fileName:	Name of the file to save.
        //   stream:	System.IO.Stream where the worksheet is saved.
        //   format:    C1.C1Excel.C1XLBook.FileFormat value that specifies the format to save 	//		the worksheet in.
//     Saves the worksheet into a stream.
        public void Save(Stream stream);
        //
	//     Saves the worksheet to a file.
        public void Save(string fileName);
        //
        
        //     Saves the worksheet into a stream.
        public void Save(Stream stream, FileFormat format);
        //
        //     Saves the worksheet to a file.
        public void Save(string fileName, FileFormat format);
```

본문 Demo의 소스코드는 다음과 같습니다. :

  

[샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/Chart_InteractionDemo.zip)


## C1PDF컨트롤로 응용프로그램에서AcroForm의PDF파일 만들기와 지원

본문에서는 어떻게 C1PDF컨트롤을 사용하는지 소개합니다. 응용 프로그램에서 AcroForm의 PDF파일을 만들고 지원합니다.

C1PDF컨트롤의 경우, 문서파일에서 사용되는 모든 명령이 .NET Graphics유형의 명령과 유사합니다. 동시에 PDF for .NET컨트롤은 안전성, 압축, 요약, 하이퍼링크 및 첨부파일 등의 기능을 제공합니다.

  

### C1PdfDocument 만들기

먼저, 도구상자에서 드래그하거나 코드를 사용하여 C1PdfDocument를 생성합니다. 생성코드는 다음과 같습니다. :

```csharp
private C1.C1Pdf.C1PdfDocument _c1pdf = new C1.C1Pdf.C1PdfDocument();
```

그 다음, 내용을 PDF문서파일에 추가합니다. 이 때 사용하는 모든 명령은 WinForms의Graphics유형에서의 명령과 서로 유사합니다. 텍스트, 이미지, 선, 사각형, 타원, 부채꼴, 원호, 둥근 사각형, 다각형, Bezier 곡선 및 더 많은 것들을 추가할 수 있습니다. C1PdfDocument의DrawString, DrawImage, DrawLine등의 방법을 참고할 수 있습니다.

  

### C1PDF의 AcroForms지원

AddField방법을 사용하여 Acrobat리스트 필드를 PDF파일에 추가할 수 있습니다. PDF for .NET컨트롤은 다음과 같은 필드유형을 지원합니다. : 텍스트박스, 체크박스, 라디오버튼, 푸시 버튼, 콤보박스, 리스트박스 및 서명필드

본문의Demo파일 중에 모든 유형에 대해 지원하는 코드가 있습니다.

예를 들어 텍스트 상자를 사용하여 PDF 파일에 텍스트 상자를 추가하는 경우 다음을 수행해야합니다.

먼저, 테스트 박스 필드를 만듭니다. 코드는 다음과 같습니다. :

```csharp
	// text box field
    rc = new RectangleF(rc.X, rc.Y + rc.Height / 10, rc.Width / 3, rc.Height / 30);
    PdfTextBox textBox1 = RenderTextBox("TextBox Sample", fieldFont, rc);
    textBox1.BorderWidth = FieldBorderWidth.Thick;
    textBox1.BorderStyle = FieldBorderStyle.Inset;
    textBox1.BorderColor = Color.Green;
```

### C1Report의 지정리포트 읽기

C1Report의 Load 방법을 통해 사용자는 읽을 보고서를 지정할 수 있습니다. 코드는 다음과 같습니다. :

```csharp
// load C1Report with selected report
c1Report1.Load(doc, reportName);
c1Report1.Sections.Header.Visible = false;
```

그리고 텍스트 박스 필드를AddField방법을 사용하여 PDF문서파일에 추가합니다. 구체적인 코드는 다음과 같습니다. ：

  

```csharp
// add text box field for fields of the PDF document
// with common parameters and default names.
// 
internal PdfTextBox RenderTextBox(string text, Font font, RectangleF rc, Color back, string toolTip)
{
    // create
    string name = string.Format("ACFTB{0}", _textBoxCount + 1);
    PdfTextBox textBox = new PdfTextBox();

    // default border
    //textBox.BorderWidth = 3f / 4;
    textBox.BorderStyle = FieldBorderStyle.Solid;
    textBox.BorderColor = SystemColors.ControlDarkDark;

    // parameters
    textBox.Font = font;
    textBox.Name = name;
    textBox.DefaultText = text;
    textBox.Text = text;
    textBox.ToolTip = string.IsNullOrEmpty(toolTip) ? string.Format("{0} ({1})", text, name) : toolTip;
    if (back != Color.Transparent && !back.IsEmpty)
    {
        textBox.BackColor = back;
    }

    // add
    _c1pdf.AddField(textBox, rc);
    _textBoxCount++;

    // done
    return textBox;
}
internal PdfTextBox RenderTextBox(string text, Font font, RectangleF rc, Color back)
{
    return RenderTextBox(text, font, rc, back, null);
}
internal PdfTextBox RenderTextBox(string text, Font font, RectangleF rc)
{
    return RenderTextBox(text, font, rc, Color.Transparent, null);
}
```

### PDF문서파일 저장

마지막으로 응용프로그램에서 생성된 PDF파일을 저장할 수 있습니다. C1PdfDocument의 Save방법을 사용하여 IO.Stream에 저장하거나 파일 속에 저장합니다. 해당 방법은 다음과 같습니다. :

  

```csharp
//
// 적요:
//     Saves the Pdf document to a System.IO.Stream.
public void Save(Stream stream);
//
// 적요:
//     Saves the Pdf document to a file.     
public void Save(string fileName);
```

본문에 첨부된Demo를 실행하려면, Form의 버튼을 클릭하여 다음과 같은PDF문서파일을 생성합니다. ：

```csharp
// add text box field for fields of the PDF document
// with common parameters and default names.
// 
internal PdfTextBox RenderTextBox(string text, Font font, RectangleF rc, Color back, string toolTip)
{
    // create
    string name = string.Format("ACFTB{0}", _textBoxCount + 1);
    PdfTextBox textBox = new PdfTextBox();

    // default border
    //textBox.BorderWidth = 3f / 4;
    textBox.BorderStyle = FieldBorderStyle.Solid;
    textBox.BorderColor = SystemColors.ControlDarkDark;

    // parameters
    textBox.Font = font;
    textBox.Name = name;
    textBox.DefaultText = text;
    textBox.Text = text;
    textBox.ToolTip = string.IsNullOrEmpty(toolTip) ? string.Format("{0} ({1})", text, name) : toolTip;
    if (back != Color.Transparent && !back.IsEmpty)
    {
        textBox.BackColor = back;
    }

    // add
    _c1pdf.AddField(textBox, rc);
    _textBoxCount++;

    // done
    return textBox;
}
internal PdfTextBox RenderTextBox(string text, Font font, RectangleF rc, Color back)
{
    return RenderTextBox(text, font, rc, back, null);
}
internal PdfTextBox RenderTextBox(string text, Font font, RectangleF rc)
{
    return RenderTextBox(text, font, rc, Color.Transparent, null);
}
```

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms5-3-1.png)

  

본문 Demo의 소스코드는 다음과 같습니다. :

  

[샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/PdfAcroform.zip)


## C1FlashCanvas을 사용하여 Flash단일 프레임 화면 또는 배경작성

본문은 C1FlashCanvas 컨트롤이 Flash 단일 프레임 화면이나 배경을 어떻게 작성하는지 소개합니다. C1FlashCanvas는 .NET 도형 유형과 비슷한 모듈입니다. .NET Graphics 유형과 완전히 동일한 도형 작성방법과 속성을 포함합니다.

  

### C1FlashCanvas 만들기

먼저, 도구상자에서 C1FlashCanvas를 창에 드래그합니다. 코드를 이용할 수도 있습니다.

예:

```csharp
private C1.C1Flash.C1FlashCanvas c1FlashCanvas1 = new C1.C1Flash.C1FlashCanvas();
```

### Flash단일 프레임 화면 작성

Flash단일 프레임 화면을 작성하기 전, C1FlashCanvas의Clear함수를 사용하여 canvas안의 모든 내용을 삭제합니다.

그리고 C1FlashCavas의Draw함수를 사용하여 필요한 도형을 작성합니다. 텍스트, 이미지, 선, 사각형, 타원, 부채꼴, 원호, 둥근 사각형, 다각형, Bezier 곡선 및 더 많은 것들을 작성할 수 있습니다. C1FlashCanvas의 DrawString, DrawImage, DrawLine등의 함수를 사용할 수 있습니다. 본문의Demo에서 각종 도형 생성에 대한 상세한 코드를 설명하고 있습니다. 아래의 예는 Rectangle로 어떻게 도형을 작성하는지 나타낸 것입니다.

코드를 사용하여 랜덤으로 Rectangle을 생성합니다. 아래의 코드 중에서 RandomRectangle함수를 사용합니다. 그리고 C1FlashCanvas의 DrawRectangle함수를 통해 canvas안에서 이 Rectangle을 작성합니다.

  

```csharp
 private Pen _pen = new Pen(Color.Black);
_pen.Color = this.panel_DrawColor.BackColor;
_pen.Width = (int)this.upd_LineWidth.Value;
for(int i = 0; i < 20; i++)
this.c1FlashCanvas1.DrawRectangle(_pen, RandomRectangle());

private Rectangle RandomRectangle()
{
	int maxWidth = this.c1FlashCanvas1.Width;
	int maxHeight = this.c1FlashCanvas1.Height;
	Point pos = new Point(_rand.Next(_minSize, maxWidth), _rand.Next(_minSize, maxHeight));
	int width = _rand.Next(_minSize, maxWidth/2);
	int height = _rand.Next(_minSize, maxHeight/2);

	return new Rectangle(pos, new Size(width, height));
}
```

### Flash배경작성

Flash배경을 작성하기 전, C1FlashCanvas의 Clear함수를 사용하여 canvas안의 모든 내용을 삭제합니다.

그리고 C1FlashCavas의 Fill함수를 사용하여 배경을 작성합니다. 사각형, 타원, 부채꼴 등의 배경을 작성할 수 있습니다. C1FlashCanvas의 FillPie, FillEllipse, FillRectangle등의 함수를 참고합니다. 본문의Demo에서 각종 도형 작성법의 상세한 코드를 설명하고 있습니다. 아래의 예는 Rectangle작성으로 어떻게 도형을 작성하는지 나타낸 것입니다.

코드를 사용하여 랜덤으로SolidBrush를 생성합니다. 아래의 코드 중에서 RandomColor함수를 참고합니다. 그리고 C1FlashCanvas의FillRectangle함수를 사용해canvas안에 이Rectangle배경을 작성합니다. 코드 속의 RandomRectangle함수는 전 단계에 코드의 정의가 있습니다.

```csharp
SolidBrush brush = new SolidBrush(Color.Black);
for(int i = 0; i < 20; i++)
{
	brush.Color = RandomColor();
	this.c1FlashCanvas1.FillRectangle(brush, RandomRectangle());
}
brush.Dispose();

private Random _rand = new Random();
private Color RandomColor()
{
return Color.FromArgb(_rand.Next(255), _rand.Next(255), _rand.Next(255), _rand.Next(255));
}
```

### SWF파일 생성

C1FlashCanvas의RenderToFile함수를 사용하여 Flash내용을 SWF파일로 작성할 수 있습니다. 코드는 다음과 같습니다. ：

this.c1FlashCanvas1.RenderToFile(tempdir + @"\c1flash_canvas_bubbles.swf");

마지막으로 System.Diagnostics.Process.Start()을 사용하여 파일을 엽니다.

Draw함수로 다음과 같이 도형을 그립니다. :

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms5-4-1.png)

Fill 함수로 다음과 같이 도형을 그립니다. :

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms5-4-2.png)

  

본문 Demo의 소스코드는 다음과 같습니다. :

  

[샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/Canvas_Bubbles.zip)


## C1Zip：표준Zip파일 처리

본문은 표준 Zip파일 만들기, 열기, 편집을 포함하는 C1Zip의 C1ZipFile유형을 사용하여 Zip 파일을 어떻게 처리하는지 소개합니다. 또한 Zip파일 속의 항목, 추가, 삭제, 압축 해제 또는 조사한 파일을 열거할 수 있습니다. 모든 폴더를 압축하고 비밀번호를 사용하여 보호 / 암호화 합니다.

C1ZipFile은 zip파일유형을 처리합니다. C1ZipFile은 C1ZipFile.Entries 속성을 가지고 있습니다. 해당 속성은 zip 파일의 항목 집합을 대표합니다.

  

### Zip파일 만들기

만들기：  C1ZipFile의 Create를 이용하여 데이터 흐름이나 드라이브 상에서 새로운 Zip파일을 만들 수 있습니다.

열기：  C1ZipFile의 Open을 이용하여 데이터 흐름이나 드라이브 상에서 Zip파일을 열 수 있습니다.

  

### Zip파일 처리

Zip파일의 항목 열거：  C1ZipFile.Entrie 집합을 통해 Zip 파일에 있는 모든 항목을 확인할 수 있습니다. 코드를 통해 파일의 상세한 정보, 각 항목의 경로 정보 및 Zip 파일의 주석을 확인할 수 있습니다.

```csharp
// fill out list
var zec = _zipFile.Entries;
listView.BeginUpdate();
foreach (C1ZipEntry ze in zec)
{
	var fa = ze.Attributes;
	var entry = new String[] 
        	{
                        FileName(ze.FileName),                      // file name, no extension
                        FileExtension(ze.FileName),                 // file extension, no dot
                        ze.Date.ToString("MM/dd/yy  HH:mm"),        // mod date/time
                        ze.SizeUncompressedLong.ToString("#,##0"),  // original size
                        ze.SizeCompressedLong.ToString("#,##0"),    // compressed size
                        AttribString(ze.Attributes),                // encode as "rahs"
			((uint)ze.CRC32).ToString(),                // CRC32 (unsigned looks better)
			ze.Comment                                  // user comment
                    };
                var lvi = new ListViewItem(entry);
                lvi.Tag = ze;
                lvi.ImageIndex = ((ze.Attributes & FileAttributes.Directory) != 0)? 0: 1;
                if (ze.IsEncrypted) lvi.ImageIndex = 3;
                listView.Items.Add(lvi);
}
```

파일추가：C1ZipFile.Entries.Add방법을 사용하여 파일을 현재 열려 있는 Zip파일에 추가할 수 있습니다.

폴더추가：C1ZipFile.Entries.AddFolder방법을 사용하여 폴더의 전체 파일을 현재 열려 있는 Zip파일에 추가할 수 있습니다.

압축：C1ZipFile.CompressionLevel속성으로 파일 항목을 취득하고 설정하여Zip파일의 압축 등급 별로 추가합니다. 먼저, C1ZipFile의 CompressionLevel속성을 설정한 후，Add나 AddFolder방법을 사용하여 파일을 Zip파일에 추가하면 설정된 압축 등급 별로 추가하게 됩니다. 감춰진 압축등급은 C1.C1Zip.CompressionLevelEnum.DefaultCompression입니다. 해당 압축등급의 유형은 다음과 같습니다. ：

  

```csharp
// 적요:
    //     Specifies the level of compression to be applied when adding entries to a
    //     C1.C1Zip.C1ZipFile.
    public enum CompressionLevelEnum
    {
        // 적요:
        //     High compression, high speed.
        DefaultCompression = -1,
        //
        // 적요:
        //     No Compression.
        NoCompression = 0,
        //
        // 적요:
        //     Low compression, highest speed.
        BestSpeed = 1,
        //
        // 적요:
        //     Highest compression, low speed.
        BestCompression = 9,
    }
```

파일삭제：C1ZipFile.Entries.Remove방법을 사용하여 현재 열려 있는Zip파일의 특정 항목을 삭제합니다.

압축 해제：C1ZipFile.Entries.Extract 방법을 사용하여 현재 열려 있는Zip파일의 압축을 해제 합니다.

파일주석：C1ZipFile.Comment속성을 사용하여 Zip파일의 관련 파일 주석을 얻거나 설정합니다.

암호 보호：C1ZipFile.Password속성은 암호를 설정하거나 취득할 수 있습니다. Zip파일 추가와 파일 항목 복구에 사용됩니다.

  

본문에 첨부된 Demo를 실행하여 Zip 파일을 엽니다. 다음과 같이 모든 항목이 표시됩니다. 그리고 메뉴를 이용해 추가, 변경, 삭제 등의 작업을 할 수 있습니다.

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms5-5-1.png)

  

본문 Demo의 소스코드는 다음과 같습니다. :

  

[샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/ZipFileDemo.zip)