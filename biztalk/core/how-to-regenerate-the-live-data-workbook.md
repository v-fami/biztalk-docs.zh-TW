---
title: "如何重新產生即時資料活頁簿 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bd3a3fa-a550-4363-bbc0-2153226509ad
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fcabebb1429fae8531753a8a3aede5595bb148f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-regenerate-the-live-data-workbook"></a>如何重新產生即時資料活頁簿
在 BAM 即時資料活頁簿所在遺失或損毀的情況下，您可以重新產生使用 BAM 管理 utiprolity 活頁簿。 若您是從 [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] 升級到 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]，這種做法也相當實用，因為 [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] 的即時資料活頁簿與 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 並不相容。  
  
 一般步驟如下：  
  
-   使用 BAM 管理公用程式，從 BAM 資料庫擷取 BAM 定義。  
  
-   重新建立樞紐分析表。 由於 get-defxml 命令所擷取的 XML 只包含活動和檢視，您必須使用 Excel 的 BAM 增益集重新建立樞紐分析表。  
  
-   重新命名樞紐分析表。 若您是從 [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] 升級到 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]，就必須執行此步驟。 這是因為必要的[!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)]，BAM 會儲存兩組 BAM 活頁簿的名稱： 顯示名稱和內部名稱。 當您擷取 BAM 定義時，XML 將包含活頁簿的內部名稱。 您必須重新命名樞紐分析表，以確保即時資料活頁簿與資料庫的連線正確。  
  
-   使用 BAM 管理公用程式重新產生即時資料活頁簿。  
  
### <a name="to-retrieve-the-bam-definition"></a>若要擷取 BAM 定義  
  
1.  按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。  
  
2.  在命令提示字元中，瀏覽至下列目錄：[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。  
  
3.  類型： **bm.exe get defxml-FileName:abc.xml**  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
### <a name="to-re-create-the-pivottable-reports"></a>若要重新建立樞紐分析表  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office**，然後按一下  **Microsoft Office Excel**。  
  
2.  按一下**增益集**索引標籤，然後選取**匯入 XML**從**BAM**下拉式清單中的**功能表命令**群組。  
  
    > [!NOTE]
    >  如果**增益集** 索引標籤不存在，請依照下列中的指示[步驟 1： 加入 Microsoft Office Excel 的 BAM 增益集](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448)新增 BAM 增益集。  
  
3.  瀏覽至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking資料夾並選取 abc.xml 檔案。  
  
4.  根據您的定義重新建立樞紐分析表。  
  
5.  儲存活頁簿。 若要這樣做，請按一下**檔案**功能表，然後再按一下**存**並提示您輸入檔案名稱時輸入 mynewbook.xls。  
  
### <a name="to-rename-the-pivottable-reports-optional"></a>若要重新命名樞紐分析表 (選擇性)  
  
1.  開啟您在擷取 BAM 定義，即可使用 「 記事本 」 時所建立的 abc.xml 檔案**啟動**，然後按一下**執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\abc.xml，，然後按一下  **確定**。  
  
2.  找出\<標題 > 標記下方\<c a p >\\< 延伸模組\>\\< OWC\>\\< 樞紐分析表檢視\>\\<樞紐分析表\>\\< 樞紐分析檢視\>\\< 標籤\>。 此標記的內容就是其中一份樞紐分析表的內部名稱。 您可以找到其他樞紐分析表報表的內部名稱找出下一步，藉以\<標題 > 標記。 開啟**mynewbook.xls**並用您位於 要重新命名樞紐分析表報表的名稱。  
  
3.  儲存更新後的活頁簿。  
  
    > [!NOTE]
    >  只有當您是從 [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] 升級到 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 時，才需要執行這個程序。  
  
### <a name="to-regenerate-the-bam-live-data-workbook"></a>若要重新產生 BAM 即時資料活頁簿  
  
1.  按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。  
  
2.  在命令提示字元中，瀏覽至下列目錄：[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。  
  
3.  類型： **bm.exe regenerate livedataworkbook-WorkbookName:mynewbook.xls**  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM](../core/managing-bam.md)   
 [BAM 管理公用程式](../core/bam-management-utility.md)   
 [適用於 Excel 的 BAM 增益集使用的需求](../core/requirements-for-using-the-bam-add-in-for-excel.md)   
 [步驟 1： 新增 BAM 增益集至 Microsoft Office Excel](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448)