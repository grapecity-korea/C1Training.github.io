---
title: ComponentOne for Winforms | 데이터 분석 및 시각화
keywords: ComponentOne, Winforms, 분석, 시각화, analysis, dataVisualization
tags: [chart, 차트, data loding, 데이터 로딩, financial graph, 금융 그래프, mathematical statistics, 수학 통계, gauge, 게이지, weather, 날씨]
last_updated: Aug 08, 2019
summary: "ComponentOne for Winforms 가 제공하는 데이터 분석 및 시각화 컨트롤을 소개합니다."
sidebar: mydoc_sidebar
permalink: c1win_dataVisualization.html
folder: mydoc
---


## 상호 작용을 위한 C1Chart 차트를 만들기

C1Chart를 이용해 조정 가능한 그래프를 만들 수 있습니다. 최종사용자가 직접 디바이스를 통해 C1Chart를 사용할 수 있습니다. 작성 요소를 이용해 최대 값이나 최소 값과 같이 마우스를 올려놓거나 클릭했을 때 툴팁에 표시되는 내용을 설정 수 있습니다. 빅 데이터나 실시간 데이터의 경우 종종 그래프로 표시할 필요가 있습니다. 끊임 없이 업데이트되는 데이터를 추가하고 스크롤이나 줌을 통해 일부 또는 일시적인 경향에 대한 정보를 얻을 수 있습니다. 3D 그래프의 C1Chart3D는 마우스 드래그를 지원합니다. 마우스를 사용하기만 하면 X, Y, Z 세 축을 임의의 방향으로 반전시킬 수 있으며 최종 사용자의 요구를 만족시킬 수 있습니다.

본문에서는 C1Chart 그래프 작성 방법과 강화된 조정기능에 대해 설명합니다. (줌, 역방향, X축 반전, 눈금)

  

### 1. C1Chart그래프 만들기

먼저, C1Chart의 조정 특성을 컨트롤합니다. 각각 마우스 반전, 눈금, 반전 및 줌을 실행합니다. 구체적인 코드는 다음과 같습니다. :

```csharp
// Enable interaction
c1Chart1.Interaction.Enabled = true;
c1Chart1.Interaction.Actions["Zoom"].Modifier = Keys.None;
c1Chart1.Interaction.Actions["Scale"].Modifier = Keys.Control;
c1Chart1.Interaction.Actions["Translate"].Modifier = Keys.Shift;
c1Chart1.Interaction.Actions["Rotate"].Modifier = Keys.Alt;
c1Chart1.Interaction.Appearance = InteractionAppearance.FillSelectionArea;
```

그 다음은 C1Chart의 서열을 만듭니다. 본문의 Demo에서는 네 개의 Series를 만들어 보았습니다. 각각 전도율, ph, 온도, 압력입니다. 이 네 개의 Series는 각각 색상으로 구별하여 표시합니다. 구체적인 코드는 다음과 같습니다. :

  

```csharp
// Create chart series
c1Chart1.ChartGroups[0].ChartData.SeriesList.Clear();
cdsTemp = c1Chart1.ChartGroups[0].ChartData.SeriesList.AddNewSeries();
cdsPress = c1Chart1.ChartGroups[0].ChartData.SeriesList.AddNewSeries();
cdsCond = c1Chart1.ChartGroups[0].ChartData.SeriesList.AddNewSeries();
cdsPh = c1Chart1.ChartGroups[0].ChartData.SeriesList.AddNewSeries();

cdsTemp.SymbolStyle.Shape = SymbolShapeEnum.None;
cdsTemp.LineStyle.Color = Color.FromArgb(150, 32, 132);
cdsTemp.LineStyle.Thickness = 2;
cdsPress.SymbolStyle.Shape = SymbolShapeEnum.None;
cdsPress.LineStyle.Color = Color.FromArgb(42, 2, 153);
cdsPress.LineStyle.Thickness = 2;
cdsCond.SymbolStyle.Shape = SymbolShapeEnum.None;
cdsCond.LineStyle.Color = Color.FromArgb(0, 114, 160);
cdsCond.LineStyle.Thickness = 2;
cdsPh.SymbolStyle.Shape = SymbolShapeEnum.None;
cdsPh.LineStyle.Color = Color.FromArgb(100, 126, 52);
cdsPh.LineStyle.Thickness = 2;
```

마지막으로 C1Chart의 축과 스크롤 바를 만듭니다. 구체적인 코드는 다음과 같습니다. :

```csharp
// Setup chart axes and scrollbar
c1Chart1.ChartArea.AxisX.ScrollBar.Scale = 0.1;
c1Chart1.ChartArea.AxisY.ScrollBar.Scale = 1.0;
c1Chart1.ChartArea.AxisX.ScrollBar.Alignment = StringAlignment.Near;
c1Chart1.ChartArea.AxisY.ScrollBar.Alignment = StringAlignment.Near;
c1Chart1.ChartArea.AxisX.ScrollBar.Appearance = ScrollBarAppearanceEnum.XP;
c1Chart1.ChartArea.AxisY.ScrollBar.Appearance = ScrollBarAppearanceEnum.XP;
c1Chart1.ChartArea.AxisX.ScrollBar.Visible = true;
c1Chart1.ChartArea.AxisY.ScrollBar.Visible = true;
c1Chart1.ChartArea.AxisY.ScrollBar.Max = 80;
c1Chart1.ChartArea.AxisY.ScrollBar.Min = 20;
c1Chart1.ChartArea.AxisX.ScrollBar.AxisScroll += new AxisScrollEventHandler(ScrollBar_AxisScroll);
```

### 2. 초기화 C1Chart，데이터 로딩

본문에 첨부된 Demo에서 C1XLBook의 Load방법을 통해 excel파일에 데이터를 로딩합니다. excel파일은 C1에 필요한 네 개의 Series (전도율, ph, 온도, 압력)의 데이터를 포함합니다. 또한 이 네 개의 Series는 실행 시 활동적으로 증가하거나 감소합니다. 즉, 사용자가 어떤 Series를 표시하는 그래프를 선택할 수 있습니다. 구체적인 것은 첨부한 Demo의 코드를 참조하실 수 있습니다.

  

### 3. C1Chart조정

[C1 Chart 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/Chart_InteractionDemo.zip)

사용자가 간단하게 C1의 조정 기능을 실현할 수 있습니다. (반전, 눈금, 역방향과 줌)  
줌: 빅 데이터나 실시간 데이터의 경우 종종 그래프로 표시할 필요가 있습니다. 끊임 없이 업데이트되는 데이터를 추가하고 스크롤이나 줌을 통해 일부 또는 일시적인 경향에 대한 정보를 얻을 수 있습니다.  
확대 참고코드：

```csharp
// Zoom out
c1Chart1.ChartArea.AxisX.ScrollBar.Scale = c1Chart1.ChartArea.AxisX.ScrollBar.Scale / _zoomScale;
c1Chart1.ChartArea.AxisY.ScrollBar.Scale = c1Chart1.ChartArea.AxisY.ScrollBar.Scale / _zoomScale;
```

X축 반전： 본문 Demo에서 사용자가 X축으로 반전되는 CheckBox를 클릭하면 C1Chart가 이를 즉시 실행할 수 있습니다. 코드도 매우 간단합니다. 한 문장만 있으면 됩니다. 다음과 같습니다.

  

```csharp
c1Chart1.ChartArea.AxisX.Reversed = chkAxisXReversed.Checked;
```

역방향： 사용자는 C1Chart의 그래프에 X축과 Y축의 역방향을 적용할 수 있습니다. Bool 유형의 C1Chart.ChartArea.Inverted 속성을 설정한 후, 다시 그래프 요소의 양식을 작성합니다. 구체적인 코드는 첨부한 Demo을 참조할 수 있습니다.

  

이뿐만 아니라 실행 시 데이터소스를 변경할 수 있어 필요한 모든 그래프를 표시할 수 있습니다. 아래 그림이 그 예시입니다.

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms4-1-1.png)

  

본문 Demo의 소스코드는 다음과 같습니다. :

  

[C1 Chart 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/Chart_InteractionDemo.zip)


## C1Chart：업종 데이터 분석（상）

[C1 Financial Chart 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/Chart-Finacial.zip)

ComponentOne Chart for WinForms는 80여종의 2D와 3D 그래프유형을 포함합니다. 코드의 그래프설계장치 없이 유연하게 그래프요소를 확정할 수 있습니다. 최종 사용자가 조정 가능한 최상의 시각효과와 우수한 마우스 추적 능력 등을 갖추고 있습니다.

ComponentOne Chart for WinForms를 사용하여 데이터 분석시스템을 업그레이드할 수 있습니다.

본문은 업종데이터 분석의 관점에서 금융그래프, 수학통계, 등고선 및 등고구역을 포함하는 C1Chart의 그래프를 소개합니다. 전반부에서는 주로 금융그래프와 데이터 통계 부분을 설명합니다.

  

### 금융그래프

금융업종은 일반적으로 캔들 차트로 가격변동을 표시하거나 HLOC그래프로 주가의 경향을 표시합니다. 이제는 ComponentOne가 제공하는 금융 그래프를 직접 WinForms응용프로그램에 드래그하여 최종 사용자에게 금융정보를 표시하고 결정을 내리도록 도울 수 있습니다. C1Chart금융그래프는 다음의 그림과 같이 표시됩니다.

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms4-2-1.png)

  

C1Chart데이터소스 설정: C1Chart.DataSource속성을 통해 데이터소스를 설정해줍니다.

C1Chart그래프유형 설정: 금융그래프는 일반적으로 캔들 차트로 가격변동을 표시하거나 HLOC그래프로 주가의 경향을 표시해야 합니다.  
이것은 C1Chart의ChartGroup.Group.ChartType열거 유형을 통해 실현할 수 있습니다. 구체적인 설정 코드는 다음과 같습니다.

```csharp
ResetChart();
//금융그래프 설정은 캔들 차트 구성입니다.
if (radChartGroups.Checked)
{
    ChartGroup g = c1Chart1.ChartGroups.Group0;
    g.ChartType = C1.Win.C1Chart.Chart2DTypeEnum.Candle;
    g.ChartData.SeriesList[0].LineStyle.Thickness = 2;
    c1Chart1.ChartGroups.Group1.Visible = true;
    c1Chart1.ChartArea.AxisY2.Visible = true;
}
//금융그래프 설정은 HiLo스위치입니다.
else if (radHiLoOpenClose.Checked)
{
    c1Chart1.ChartGroups.Group0.ChartType = C1.Win.C1Chart.Chart2DTypeEnum.HiLoOpenClose;
}
//금융그래프 설정은 캔들 차트입니다.
else if (radCandle.Checked)
{
    ChartGroup g = c1Chart1.ChartGroups.Group0;
    g.ChartType = C1.Win.C1Chart.Chart2DTypeEnum.Candle;
    g.ChartData.SeriesList[0].LineStyle.Thickness = 2;
}
//금융그래프 설정은 HiLo입니다.
else
{
    c1Chart1.ChartGroups.Group0.ChartType = C1.Win.C1Chart.Chart2DTypeEnum.HiLo;
}
```

그 다음은 C1Chart의 서열을 만듭니다. 본문의 Demo에서는 네 개의 Series를 만들어 보았습니다. 각각 전도율, ph, 온도, 압력입니다. 이 네 개의 Series는 각각 색상으로 구별하여 표시합니다. 구체적인 코드는 다음과 같습니다. :

  

```csharp
// Create chart series
c1Chart1.ChartGroups[0].ChartData.SeriesList.Clear();
cdsTemp = c1Chart1.ChartGroups[0].ChartData.SeriesList.AddNewSeries();
cdsPress = c1Chart1.ChartGroups[0].ChartData.SeriesList.AddNewSeries();
cdsCond = c1Chart1.ChartGroups[0].ChartData.SeriesList.AddNewSeries();
cdsPh = c1Chart1.ChartGroups[0].ChartData.SeriesList.AddNewSeries();

cdsTemp.SymbolStyle.Shape = SymbolShapeEnum.None;
cdsTemp.LineStyle.Color = Color.FromArgb(150, 32, 132);
cdsTemp.LineStyle.Thickness = 2;
cdsPress.SymbolStyle.Shape = SymbolShapeEnum.None;
cdsPress.LineStyle.Color = Color.FromArgb(42, 2, 153);
cdsPress.LineStyle.Thickness = 2;
cdsCond.SymbolStyle.Shape = SymbolShapeEnum.None;
cdsCond.LineStyle.Color = Color.FromArgb(0, 114, 160);
cdsCond.LineStyle.Thickness = 2;
cdsPh.SymbolStyle.Shape = SymbolShapeEnum.None;
cdsPh.LineStyle.Color = Color.FromArgb(100, 126, 52);
cdsPh.LineStyle.Thickness = 2;
```

### 수학통계

C1Chart은 이산 데이터 속에 포함된 평균, 최빈수, 평균분포 등의 통계치를 연구할 때 편리합니다. 산포도와 히스토그램을 사용하여 이산 데이터를 분석하여 더욱 편리하게 사용할 수 있고 데이터 샘플 속에서 필요한 정보를 찾는 데도 도움을 줍니다. C1Chart 데이터 통계치 히스토그램은 아래에 표시된 것과 같습니다. 이것은 산포 데이터가 십자선 거리의 빈도 히스토그램까지 이른 것입니다.

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms4-2-2.png)

  

C1Chart그래프 만들기： 본문의 수리통계 demo 에서 탭과 산포데이터로 첫 번째 ChartGroup에 C1Chart을 만들고 두 번째 ChartGroup에 Histogram을 만듭니다. 이때 두 번째의 ChartGroup에는 데이터를 추가하지는 않습니다. 자세한 코드는 Demo의Histogram을 참고합니다.

  

C1Chart의Histogram만들기：  ChartHistogram을 사용하여 대상의 DisplayType 속성을 통해 히스토그램, 빈도그래프, 스텝 빈도그래프 형식으로 간격과 수량을 표시합니다. Demo에서는 이산 데이터가 두 번째 ChartGroup에 Histogram을 만들고 각 산포 데이터를 바탕으로 탭 되는 교차 거리를 표시합니다. 코드는 다음을 참고합니다. ;

  

```csharp
//create a Histogram in the second chart group using the scatter data
//and the distance from the marker intersection as data for the histogram.
ChartGroup cg = c1Chart1.ChartGroups[1];

//start by adding a Normal (Gaussian) distribution curve.  This is available
//as a convenient reference to compare the histogram shape.
NormalCurve nc = cg.Histogram.NormalDisplay;
nc.FillStyle.Alpha = 64;
nc.FillStyle.Color1 = Color.Yellow;
nc.Visible = c1Chart1.ChartGroups[1].Histogram.NormalDisplay.Visible;

cg.ChartType = Chart2DTypeEnum.Histogram;

ChartDataSeries cds = cg.ChartData.SeriesList.AddNewSeries();
cds.FitType = FitTypeEnum.Spline;
cds.FillStyle.Alpha = 64;
cds.FillStyle.Color1 = Color.Blue;

cds.Histogram.IntervalCreationMethod = IntervalMethodEnum.SemiAutomatic;
cds.Histogram.DisplayType = DisplayTypeEnum.Histogram;
cds.Histogram.IntervalStart = 0;
cds.Histogram.IntervalWidth = 10;
cds.Histogram.IntervalNumber = 10;

C1.Win.C1Chart.Label lab = c1Chart1.ChartLabels.LabelsCollection.AddNewLabel();
lab.AttachMethod = AttachMethodEnum.DataCoordinate;
lab.AttachMethodData.X = 100;
lab.AttachMethodData.Y = 0;
lab.AttachMethodData.GroupIndex = 0;
lab.Offset = 50;
lab.Name = "overflow";
lab.Text = "";
lab.Compass = LabelCompassEnum.South;
lab.Visible = true;
```

Histogram데이터 기입：  Demo에서는 기입한 Histogram 데이터 탭에 따릅니다.

```csharp
//get the Target Coordinates
double xtarget = carea.AxisX.ValueLabels[0].NumericValue;
double ytarget = carea.AxisY.ValueLabels[0].NumericValue;

//get the data point coordinates from the chart.
ChartDataSeries cds = c1Chart1.ChartGroups[0].ChartData.SeriesList[0];
PointF[] cdata = (PointF[])cds.PointData.CopyDataOut();

//find the distance from each scatter point to the target point.
int n = cdata.Length;
double[] distances = (double[])Array.CreateInstance(typeof(double), n);
for (int i = 0; i < n; i++)
{
    double dx = cdata[i].X - xtarget;
    double dy = cdata[i].Y - ytarget;
    distances[i] = Math.Sqrt(dx * dx + dy * dy);
}

//add the data to the Histogram chart series in ChartGroup(1).
cds = c1Chart1.ChartGroups[1].ChartData.SeriesList[0];
cds.Y.CopyDataIn(distances);

//report the statistics of the distance data.
lblStats.Text = "거리통계: " +
    "  평균치: " + cds.Y.Statistics.Mean.ToString("0.000") +
    "  중위수: " + cds.Y.Statistics.Median.ToString("0.000") +
    "  표준편차: " + cds.Y.Statistics.StdDev.ToString("0.000");

//set the overflow label.
int overflow = (int)cds.Histogram.AboveIntervalCount;
string msg = "";
if (overflow > 0)
{
    msg = "수량 > " + carea.AxisX.Max.ToString() + " = " + overflow.ToString();
}
c1Chart1.ChartLabels["overflow"].Text = msg;
```

여기까지 본문에서 금융 그래프와 수리통계 그래프를 설명했습니다. 이 그래프들은 사용자로 하여금 직관적으로 필요한 분야의 데이터 분석하여 신속하게 결정하도록 도와줍니다. 본문의 후반부에서는 등고선과 등고 구역 그래프 작성에 대해 설명하겠습니다.

본문(상)의 Demo소스코드는 다음과 같습니다. :

  

[C1 Financial Chart 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/Chart-Finacial.zip)


## C1Chart：업종 데이터 분석（하）

[C1 3D Chart 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/Chart2.zip)

상편에서 우리는 금융그래프와 데이터 통계를 포함하는 C1Chart의 그래프를 설명했습니다. 본문 하편에서는 주로 업종데이터분석의 등고선과 등고 지역을 설명합니다.

ComponentOne Chart for WinForms는 80여종의 2D와 3D 그래프유형을 포함합니다. 코드의 그래프설계장치 없이 유연하게 그래프요소를 확정할 수 있습니다. 최종 사용자가 조정 가능한 최상의 시각효과와 우수한 마우스 추적 능력 등을 갖추고 있습니다.

ComponentOne Chart for WinForms를 사용하여 데이터 분석 시스템을 업그레이드할 수 있습니다.

  

등고선과 등고지역

  

C1Chart3D컨트롤은 자동으로 등고선을 생성할 수 있고 데이터에 근거하여 구역을 구분합니다. 온도, 해발고도, 대기질량 등 전문적인 데이터를 표기하는 데 사용할 수 있습니다. C1Chart3D는 내장된 크로마토그램이나 자체정의로 각 지역에 색을 입혀줍니다. C1Chart3D는 각 구역 간 자동 색상 조절을 신속하고 원활하게 할 수 있습니다.

그 밖에 조정 기능을 강화하여 Chart의 마우스 회전, 리프팅, 이동 및 보관을 포함하는 내장된 조정 기능을 제공합니다.

  

C1Chart3D바인딩 데이터 :  Chart3DDataSetGrid의 XML데이터 바인딩은 등고선 자동 생성에 사용됩니다. 구체적인 코드는 다음과 같습니다. :

```csharp
Chart3DDataSetGrid grid = c1Chart3D1.ChartGroups.Group0.ChartData.SetGrid;
IList rows = categorySales1.List;
Chart3DAxis x = c1Chart3D1.ChartArea.AxisX;
Chart3DAxis y = c1Chart3D1.ChartArea.AxisY;
Chart3DAxis z = c1Chart3D1.ChartArea.AxisZ;
grid.RowCount = rows.Count;
grid.ColumnCount = 4;

for (int i = 0; i < rows.Count; i++)
{
    DataRowView view = rows[i] as DataRowView;
    DataRow r = view.Row;
    grid[0, i] = System.Convert.ToDouble(r[1]);
    grid[1, i] = System.Convert.ToDouble(r[2]);
    grid[2, i] = System.Convert.ToDouble(r[3]);
    grid[3, i] = System.Convert.ToDouble(r[4]);
    y.ValueLabels.Add(i, r[0].ToString());
}

x.ValueLabels.Add(0, "Q1");
x.ValueLabels.Add(1, "Q2");
x.ValueLabels.Add(2, "Q3");
x.ValueLabels.Add(3, "Q4");
x.AnnoMethod = AnnotationMethodEnum.ValueLabels;
x.AnnoPosition = AnnoPositionEnum.Both;

x.MajorGrid.IsOnXYPlane = true;
x.MajorGrid.IsOnXZPlane = true;
x.MajorGrid.Style.Color = SystemColors.ControlDarkDark;

y.AnnoMethod = AnnotationMethodEnum.ValueLabels;
y.AnnoRotated = true;
y.AnnoPosition = AnnoPositionEnum.Both;

y.MajorGrid.IsOnXYPlane = true;
y.MajorGrid.IsOnYZPlane = true;
y.MajorGrid.Style.Color = SystemColors.ControlDarkDark;

z.AnnoFormat = FormatEnum.NumericManual;
z.AnnoFormatString = "#,";
z.Text = "$1,000's";
z.UnitMajor = z.UnitMinor;

z.MajorGrid.IsOnXZPlane = true;
z.MajorGrid.IsOnYZPlane = true;
z.MajorGrid.Style.Color = SystemColors.ControlDarkDark;
```

C1Chart3D의 줌 조정 :  Chart3D의 Scal을 통해 줌 비율을 조정합니다. 코드는 다음과 같습니다. :

  

```csharp
//Adjust zoom level
c1Chart3D1.ChartArea.View.ViewportScale = 1.4f;
c1Chart3D1.ChartArea.View.ViewportHorizontalShift = .15f;
c1Chart3D1.ChartArea.View.ViewportVerticalShift = -.17f;
```

C1Chart3D등고선의 조정：  설정을 통해 C1Chart3D는 마우스 회전, 리프팅, 이동 및 보관을 실현할 수 있습니다. Demo에서는 마우스로 드래그하거나 TrackBar를 조정하여 회전할 수 있습니다. 코드는 아래와 같습니다. :

```csharp
private System.Windows.Forms.TrackBar trkYAxis; 
private void trkXAxis_Scroll(object sender, EventArgs e) 
{ 
    c1Chart3D1.ChartArea.View.RotationX = trkXAxis.Value; 
} 
private void trkYAxis_Scroll(object sender, EventArgs e) 
{ 
    c1Chart3D1.ChartArea.View.RotationY = trkYAxis.Value; 
} 
private void trkZAxis_Scroll(object sender, EventArgs e) 
{ 
    c1Chart3D1.ChartArea.View.RotationZ = trkZAxis.Value; 
}
```

상기 조작을 통해 자동으로 생성된 등고선 그래프는 다음과 같습니다. 온도, 해발, 대기질량 영역 등의 전문적인 데이터를 표기하는데 사용됩니다.

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms4-3-1.png)

  

본문 Demo의 소스코드는 다음과 같습니다. :

  

[C1 3D Chart 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/Chart2.zip)


## C1 Gauge：데이터 바인딩을 통한 날씨 표시

날씨 데이터나 메시지 센터 또는 KPI게시판을 만들고자 하는 경우, 일목요연하게 중요 데이터를 파악할 수 있어야 합니다. C1Gauge를 폼에 드래그하여 데이터 값만 입력하면 간단하게 완성할 수 있습니다.

본문에서는 어떻게 C1Gauge컨트롤을 사용하여 데이터와 게이지를 결합하여 날씨 데이터를 표시하는지 소개합니다.

  

### 1. C1Gauge를 폼에 드래그

툴바에서 C1Gauge를 폼에 드래그 합니다. 새로운 게이지라이브러리 다이얼로그창이 팝업 되면 그 속에서 원하는 게이지를 하나 선택합니다. 방사형 및 선형이 있습니다. 방사형 게이지는 원형, 나선형, 호선형, 폴딩식 또는 반원일 수 있으며 선형 게이지는 수평, 수직 또는 경사형입니다.

게이지 라이브러리 다이얼로그창은 다음과 같습니다. ：

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms4-4-1.png)

  

본문의 Demo에서는 C1Gauge컨트롤을 사용하여 많은 게이지 조합을 하나의 팩으로 구성합니다. 각 게이지 컨트롤은 겹치거나 배열을 설정할 수 있습니다. 또 임의의 방식으로 게이지 컨트롤의 크기를 조정할 수 있고 각 게이지 컨트롤마다 가로세로 비율과 상대위치를 유지할 수도 있습니다.

  

### 2. 데이터 바인딩 게이지

C1Gauge는 표준 .NET 데이터 바인딩 기술을 사용합니다. 즉, C1Gauge.DataSource로 C1Gauge컨트롤을 데이터소스에 바인딩 할 수 있습니다. 또 DataBindings로 각기 다른 지침을 각각의 데이터 필드에 바인딩 할 수도 있습니다. XML, Access, SQL Server, Oracle 내에서 Visual Studio .NET 데이터를 대상으로 IList, IList<T>및 IEnumerable<T> 포트를 실현합니다. C1Gauge는 모든 지원을 제공합니다.

각기 다른 지침을 각각의 데이터 필드에 바인딩하는 C1Gauge.DataBindings.Add방법은 다음과 같습니다. :

```csharp
// 변수:
//   propertyName: 바인딩할 컨트롤 속성의 명칭
//   dataSource: 데이터소스를 표시한 System.Object。
//   dataMember: 바인딩 할 속성이나 리스트.
//   formattingEnabled: 양식화로 데이터를 표시하는 경우라면 true；아니라면 false。
//   updateMode: System.Windows.Forms.DataSourceUpdateMode 값 중 하나。
//   nullValue: 데이터 소스 값이 System.DBNull 일 때, 바인딩에 사용되는 컨트롤 속성인System.Object。
//   formatString: 하나 또는 여러 개 양식 설명부호가 표시 값을 어떻게 표시하는가
//   formatInfo: 감춘 양식설정을 다시 기입하는 System.IFormatProvider 의 실현.
//   binding: 추가할 System.Windows.Forms.Binding。

// 적요: 지정한 System.Windows.Forms.Binding 을 집합에 추가합니다.
public void Add(Binding binding);

public Binding Add(string propertyName, object dataSource, string dataMember);

public Binding Add(string propertyName, object dataSource, string dataMember, bool formattingEnabled);

public Binding Add(string propertyName, object dataSource, string dataMember, bool formattingEnabled, DataSourceUpdateMode updateMode);
    
public Binding Add(string propertyName, object dataSource, string dataMember, bool formattingEnabled, DataSourceUpdateMode updateMode, object nullValue);
    
public Binding Add(string propertyName, object dataSource, string dataMember, bool formattingEnabled, DataSourceUpdateMode updateMode, object nullValue, string formatString);
    
public Binding Add(string propertyName, object dataSource, string dataMember, bool formattingEnabled, DataSourceUpdateMode updateMode, object nullValue, string formatString, IFormatProvider formatInfo);
```

### 3. 게이지 속성 설정

C1Gauge컨트롤의 아무 곳이나 더블 클릭하거나 한 번 클릭하면 에디터가 팝업 되어 속성을 빠르게 편집할 수 있습니다.

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms4-4-2.png)

  

### 4. 바인딩 내용을 게이지 날씨 데이터로 전환

[C1 날씨 게이지 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/C1Gauge-Weather.zip)

본문의 Demo 게이지가 표시하는 날씨는 바인딩 한 날씨 데이터를 전환해야 합니다. 예를 들어 맑은 날, 비 오는 날 등 적합한 수치로 전환합니다. 코드는 다음을 참고해 주시기 바랍니다.

```csharp
//handle custom binding for Events gauge (sun, rain, thunderstorm, snow)
string events = (weatherData1.Current as DataRowView)["events"].ToString();
string[] eventsArray = events.Split('-');
if (eventsArray.Length == 0)
{
    eventsgauge.Value = 3;
    eventsgauge.MorePointersValue_0 = 3;
    eventsgaugeMorePointersValue_1 = 3;
}
else if (eventsArray.Length == 1)
{
    Eventsgauge.Value = WeatherEventConverter(eventsArray[0]);
    eventsgauge.MorePointersValue_0 = WeatherEventConverter(eventsArray[0]);
    eventsgaugeMorePointersValue_1 = WeatherEventConverter(eventsArray[0]);
}
else if (eventsArray.Length == 2)
{
    eventsgauge.Value = WeatherEventConverter(eventsArray[0]);
    eventsgauge.MorePointersValue_0 = WeatherEventConverter(eventsArray[1]);
    eventsgauge.MorePointersValue_1 = WeatherEventConverter(eventsArray[0]);
}
else if (eventsArray.Length == 3)
{
    eventsgaege.Value = WeatherEventConverter(eventsArray[0]);
    eventsgaege.MorePointersValue_0 = WeatherEventConverter(eventsArray[1]);
    eventsgaege.MorePointersValue_1 = WeatherEventConverter(eventsArray[2]);
}
```

Demo를 실행하면 아래 그림과 같은 날씨게이지를 확인할 있습니다. 바인딩 데이터의 다른 행을 선택하면 게이지가 바인딩 데이터에 따라 변화를 일으키게 됩니다.

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms4-4-3.png)

  

본문 Demo의 소스코드는 다음과 같습니다. :

  

[C1 날씨 게이지 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/C1Gauge-Weather.zip)