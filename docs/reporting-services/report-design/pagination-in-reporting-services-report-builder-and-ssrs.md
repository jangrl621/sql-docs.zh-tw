---
title: Reporting Services 中的分頁 (報表產生器與 SSRS) | Microsoft Docs
ms.date: 07/26/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: e0894b0d-dc5b-4a75-8142-75092972a034
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 507aeab666f1849b9216b22e90dfee3d21f92694
ms.sourcegitcommit: a154b3050b6e1993f8c3165ff5011ff5fbd30a7e
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68632023"
---
# <a name="pagination-in-reporting-services-report-builder--and-ssrs"></a>Reporting Services 中的分頁 (報表產生器與 SSRS)
  分頁指的是報表內的頁數，以及如何在這些頁面上排列報表項目。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的分頁會根據您用於檢視和傳遞報表的轉譯延伸模組而有所不同。 當您在報表伺服器上執行報表時，報表會使用 HTML 轉譯器。 HTML 會遵循特定的一組分頁規則。 例如，如果您將相同的報表匯出至 PDF，系統就會使用 PDF 轉譯器，並套用另一組不同的規則，因此，報表的分頁就會不同。 若要為使用者成功設計容易閱讀的報表，並針對計畫用於傳遞報表的轉譯器最佳化該報表，您必須了解用於控制 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中之分頁的規則。  
  
 本主題討論實體頁面大小與報表配置，對手動分頁符號轉譯器轉譯報表的影響。 您可以使用 **[報表屬性]** 窗格、 **[屬性]** 窗格或 **[版面設定]** 對話方塊來設定屬性，藉此修改實際頁面大小和邊界，並且將報表分為資料行。 按一下報表主體外面的藍色區域即可存取 **[報表屬性]** 。 按一下 [主資料夾] 索引標籤上的 **[執行]** ，然後按一下 [執行] 索引標籤上的 **[版面設定]** ，即可存取 **[版面設定]** 對話方塊。  
  
> [!NOTE]  
>  如果您將報表設計成單頁寬度，但它轉譯跨多個頁面，請確認報表主體 (包括邊界) 的寬度不超出實體頁面大小的寬度。 為避免將空頁面加入到您的報表，可以將容器邊角向左拖曳，來縮減容器的大小。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="the-report-body"></a>報表主體  
 報表主體是在設計介面上會顯示為空格的矩形容器。 它可以擴張或縮小以容納包含在其中的報表項目。 報表主體不會反映實體頁面大小，而且事實上，報表主體的擴張可以超出實體頁面大小的界限而跨越多個報表頁面。 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]、Word、HTML 和 MHTML 之類的某些轉譯器會轉譯根據頁面內容而擴張或縮小的報表。 以這些格式轉譯的報表會針對螢幕檢視 (例如在網頁瀏覽器中) 最佳化。 這些轉譯器會在需要時加入垂直分頁符號。  
  
 您可以設定報表主體的格式，讓其包含框線色彩、框線樣式，以及框線寬度。 您也可以加入背景色彩和背景影像。  
  
## <a name="the-physical-page"></a>實體頁面  
 實體頁面大小就是紙張大小。 您針對報表指定的紙張大小會控制轉譯報表的方式。 以手動分頁符號格式轉譯的報表會根據實體頁面大小水平和垂直插入分頁符號，就可以在使用手動分頁符號檔案格式列印或檢視時，提供最佳化的閱讀經驗。 以軟分頁符號格式轉譯的報表會根據實體頁面大小水平插入分頁符號，就可以在使用網頁瀏覽器檢視時，提供最佳化的閱讀經驗。  
  
 根據預設，頁面大小為 8.5 x 11 英吋，但是您可以使用 [報表屬性]  窗格、[版面設定]  對話方塊，或變更 [屬性]  窗格中的 PageHeight 和 PageWidth 屬性來變更這個大小。 頁面大小不會擴張或縮小來容納報表主體的內容。 如果您要讓報表出現在單頁上，報表主體內的所有內容都必須容納在實體頁面中。 如果無法容納在單頁中，而且您使用手動分頁符號格式，則報表將需要額外的頁面。 如果報表主體的擴張超過實體頁面的右邊緣，則會水平插入分頁符號。 如果報表主體的擴張超過實體頁面的下邊緣，則會垂直插入分頁符號。  
  
 如果您要覆寫報表中定義的實體頁面大小，您可以針對要用於匯出報表的特定轉譯器，使用 [裝置資訊] 設定來指定實體頁面大小。 如需詳細資訊，請參閱 [Reporting Services 裝置資訊設定](../device-information-settings-for-rendering-extensions-reporting-services.md)。  
  
### <a name="margins"></a>邊界  
 邊界會從實體頁面尺寸的邊緣向內繪製到指定的邊界設定。 如果報表項目擴充到邊界區域，則該項目會遭到裁剪，因此不會轉譯重疊的區域。 如果您指定的邊界大小會使頁面的水平或垂直寬度等於零，邊界設定會預設為零。 您可以使用 [報表屬性]  窗格、[版面設定]  對話方塊，或變更 [屬性]  窗格中的 TopMargin、BottomMargin、LeftMargin 和 RightMargin 屬性來指定邊界。 如果您要覆寫報表中定義的邊界大小，您可以針對要用於匯出報表的特定轉譯器，使用 [裝置資訊] 設定來指定邊界大小。  
  
 在配置邊界、資料行間距和頁首與頁尾的空間後剩餘的實體頁面區域稱為 *「可用的頁面區域」* (Usable Page Area)。 只有在您以手動分頁符號轉譯器格式轉譯與列印報表時，才會套用邊界。 下列影像指出實體頁面的邊界與可用的頁面區域。  
  
 ![具有邊界與可用區域的實體頁面。](../../reporting-services/report-design/media/rspagemargins.gif "具有邊界與可用區域的實體頁面。")  
  
### <a name="newsletter-style-columns"></a>新聞稿樣式資料行  
 您的報表可以分割為多個資料行 (例如，新聞稿中的資料行)，而且這些資料行會被視為在相同實體頁面上轉譯的邏輯頁面。 這些資料行會從左到右、從上到下排列，而且在每個資料行之間，會以空格分隔。 如果報表分割為一個以上的資料行，每個實體頁面都會垂直分割為多個資料行，而且其中每個資料行都會被視為一個邏輯頁面。 例如，假設您的實體頁面上有兩個資料行。 報表的內容會先填滿第一個資料行，然後再填滿第二個資料行。 如果報表無法完整容納在前兩個資料行內，報表會先填滿第一個資料行，然後再填滿下一頁的第二個資料行。 資料行會從左到右，從上到下，繼續填滿，直到所有報表項目都轉譯完成為止。 如果您指定的資料行大小會使頁面的水平寬度或垂直寬度等於零，資料行間距會預設為零。  
  
 您可以使用 [報表屬性]  窗格、[版面設定]  對話方塊，或變更 [屬性]  窗格中的 TopMargin、BottomMargin、LeftMargin 和 RightMargin 屬性來指定資料行。 如果您要使用未定義的邊界大小，您可以針對要用於匯出報表的特定轉譯器，使用 [裝置資訊] 設定來指定邊界大小。 只有在您以 PDF 或影像格式轉譯與列印報表時，才會套用資料行。 下列影像指出包含資料行之頁面的可用頁面區域。  
  
 ![顯示資料欄的實體頁面。](../../reporting-services/report-design/media/rspagecolumns.gif "顯示資料欄的實體頁面。")  
  
## <a name="page-breaks-and-page-names"></a>分頁和頁面名稱  
 當報表中包含頁面名稱時，報表可能會更容易閱讀，其資料也會更容易稽核及匯出。 Reporting Services 報表中提供報表及 Tablix 資料區域 (資料表、矩陣和清單) 的屬性、群組和矩形，可控制重新編頁、重設頁碼，並在分頁時提供新的報表頁面名稱。 不論報表以何種格式轉譯，這些功能都可以加強報表運作，尤其是在將報表匯出至 Excel 活頁簿時特別有用。  
  
 InitialPageName 屬性提供報表的初始頁面名稱。 如果您的報表不包含要分頁的頁面名稱，則初始頁面名稱會用於分頁所建立的所有新頁面。 使用初始頁面名稱不需要它。  
  
 轉譯的報表可以針對分頁所造成的新頁面，提供新的頁面名稱。 若要提供頁面名稱，您要設定資料表、矩陣、清單、群組或矩形的 PageName 屬性。 不需要您在分頁時指定頁面名稱。 如果您沒有指定，就會改用 InitialPageName 的值。 如果 InitialPageName 也是空白的，則新頁面沒有名稱。  
  
 Tablix 資料區 (資料表、矩陣和清單)、群組和矩形支援分頁。  
  
 分頁包含下列屬性：  
  
-   BreakLocation 會針對啟用分頁的報表元素，提供分頁的位置：開頭、結尾，或開頭和結尾。 若是群組，BreakLocation 可以位於群組之間。  
  
-   Disabled 會指出是否將分頁套用至報表元素。 如果這個屬性評估為 True，則會忽略分頁。 如果使用這個屬性，可以根據報表執行時的運算式，以動態方式停用分頁。  
  
-   ResetPageNumber 會指出分頁時，是否應該將頁碼重設為 1。 如果這個屬性評估為 True，則會重設頁碼。  
  
 您可以在 [Tablix 屬性]  、[矩形屬性]  或 [群組屬性]  對話方塊中設定 BreakLocation 屬性，但是您必須在報表產生器的 [屬性] 窗格中設定 Disabled、ResetPageNumber 和 PageName 屬性。 如果 [屬性] 窗格中的屬性是依類別目錄組織，您將要在 **[分頁]** 類別目錄中尋找屬性。 若是群組， **[分頁]** 類別目錄位於 **[群組]** 類別目錄內。  
  
 您可以使用常數和簡單或複雜的運算式來設定 Disabled 和 ResetPageNumber 屬性的值。 不過，您無法搭配 BreakLocation 屬性使用運算式。 如需撰寫和使用運算式的詳細資訊，請參閱[運算式 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)。  
  
 在您的報表中，您可以使用 **Globals** 集合，撰寫參考目前頁面名稱或頁碼的運算式。 如需詳細資訊，請參閱[內建的全域和使用者參考 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/built-in-collections-built-in-globals-and-users-references-report-builder.md)。  
  
### <a name="naming-excel-worksheet-tabs"></a>命名 Excel 工作表頁籤  
 當您將報表匯出至 Excel 活頁簿時，這些屬性相當實用。 當您匯出報表時，使用 InitialPage 屬性來指定工作表索引標籤名稱的預設名稱，並使用分頁和 PageName 屬性，為每個工作表提供不同的名稱。 由分頁所定義的每個新的報表頁面都會匯出至由 PageName 屬性的值所命名的不同工作表。 如果 PageName 是空白的，但是報表有一個初始頁面名稱，則 Excel 活頁簿中的所有工作表都會使用相同的名稱，也就是初始頁面名稱。  
  
 如需報表匯出至 Excel 時，這些屬性如何運作的詳細資訊，請參閱[匯出至 Microsoft Excel &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md)。  
  
## <a name="see-also"></a>另請參閱  
 [頁面配置和轉譯 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/page-layout-and-rendering-report-builder-and-ssrs.md)  
  
  
