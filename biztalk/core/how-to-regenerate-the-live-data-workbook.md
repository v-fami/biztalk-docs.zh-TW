---
title: 重新產生即時資料活頁簿 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4bd3a3fa-a550-4363-bbc0-2153226509ad
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7eda4dcb210f3d0272cdb0f04da8ae7d7ef2942d
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50753142"
---
# <a name="regenerate-the-live-data-workbook"></a>重新產生即時資料活頁簿
在 BAM 即時資料活頁簿其中遺失或損毀的情況下，您可以重新產生活頁簿使用 BAM 管理 utiprolity。 此程序也很有用的當您將升級從舊版 BizTalk Server。
  
 一般步驟如下：  
  
-   使用 BAM 管理公用程式，從 BAM 資料庫擷取 BAM 定義。  
  
-   重新建立樞紐分析表。 由於 get-defxml 命令所擷取的 XML 只包含活動和檢視，您必須使用 Excel 的 BAM 增益集重新建立樞紐分析表。  
  
-   重新命名樞紐分析表。 此步驟可能需要您從舊版 BizTalk Server 升級。 某些版本中，BAM 會儲存兩組為 BAM 活頁簿的名稱： 的顯示名稱和內部名稱。 當您擷取 BAM 定義時，XML 將包含活頁簿的內部名稱。 您必須重新命名樞紐分析表，以確保即時資料活頁簿與資料庫的連線正確。  
  
-   使用 BAM 管理公用程式重新產生即時資料活頁簿。  
  
## <a name="retrieve-the-bam-definition"></a>擷取 BAM 定義  
  
1. 按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2. 在命令提示字元中，瀏覽至下列目錄： [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking。  
  
3. 類型： **bm.exe get defxml-FileName:abc.xml**  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
## <a name="recreate-the-pivottable-reports"></a>重新建立樞紐分析表報表  
  
1. 按一下 **開始**，指向**所有程式**，指向**Microsoft Office**，然後按一下**Microsoft Office Excel**。  
  
2. 按一下 **增益集**索引標籤，然後按**匯入 XML**從**BAM**下拉式清單中的**功能表命令**群組。  
  
   > [!NOTE]
   >  如果**增益集**索引標籤不存在，請依照下列中的指示[步驟 1： 加入 Microsoft Office Excel 的 BAM 增益集](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448)新增 BAM 增益集。  
  
3. 瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking 資料夾，然後選取 abc.xml 檔案。  
  
4. 根據您的定義重新建立樞紐分析表。  
  
5. 儲存活頁簿。 若要這樣做，請按一下**檔案**功能表，然後再按一下**另存新檔**和檔案名稱出現提示時輸入 mynewbook.xls。  
  
## <a name="rename-the-pivottable-reports-optional"></a>重新命名樞紐分析表報表 （選擇性）  

> [!NOTE]
> 如果您要升級從舊版的 BizTalk Server，此步驟可能只是必要。 

1. 開啟您在擷取 BAM 定義，即可使用 「 記事本 」 時所建立的 abc.xml 檔案**開始**，再按一下**執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking\abc.xml，，然後按一下**確定**。  
  
2. 找出\<Caption\>標記下\<<bamdefinition>\<extension>\<owc>\<pivottableview>\<pivottable>\<pivotview>\<label>\>\\< 延伸模組\>\\< OWC\>\\< 樞紐分析表檢視\> \\< 樞紐分析表\>\\< 樞紐分析檢視\>\\< 標籤\>。 此標記的內容就是其中一份樞紐分析表的內部名稱。 您可以找到其他樞紐分析表報表的內部名稱找出下一步，藉以\<標題\>標記。 開啟**mynewbook.xls**並使用您找到要重新命名樞紐分析表的名稱。  
  
3. 儲存更新後的活頁簿。    
 
  
## <a name="regenerate-the-bam-live-data-workbook"></a>重新產生 BAM 即時資料活頁簿  

> [!NOTE]
>  以系統管理權限執行此工具。  


1. 按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2. 在命令提示字元中，瀏覽至下列目錄： [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking。  
  
3. 類型： **bm.exe 重新產生 livedataworkbook-WorkbookName:mynewbook.xls**  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM](../core/managing-bam.md)   
 [BAM 管理公用程式](../core/bam-management-utility.md)   
 [適用於 Excel 的 BAM 增益集使用的需求](../core/requirements-for-using-the-bam-add-in-for-excel.md)   
 [步驟 1： 將 BAM 增益集新增至 Microsoft Office Excel](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448)
