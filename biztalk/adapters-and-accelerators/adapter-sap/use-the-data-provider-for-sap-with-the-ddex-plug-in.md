---
title: 使用 Data Provider for SAP 與 DDEX 外掛程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DDEX plug-in
- DDEX plug-in, Data Provider for SAP
- Data Provider for SAP, using with DDEX plug-in
ms.assetid: b16c8634-172a-4630-87ed-2073a75afdec
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 344467367e5745ab089c3f70be017759d22ba8b1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970687"
---
# <a name="use-the-data-provider-for-sap-with-the-ddex-plug-in"></a>使用 Data Provider for SAP 與 DDEX 外掛程式
如果您選擇要安裝[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]連同[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝，安裝程式安裝[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]DDEX 外掛程式。 您可以使用此外掛程式來瀏覽 SAP 物件使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 本節提供使用的 DDEX 外掛程式的相關資訊。  
  
 您可以使用外掛程式，以建立與 SAP 系統的連線能力的 SAP 系統從新增資料表，並新增從 SAP 系統的函式模組。 您加入的資料表和函式的模組，使用 Visual Studio 外掛程式之後，新加入的資料表和函式模組會反映在 SAPDiscoveredObjects.xml 檔案中。 如需有關這個檔案的詳細資訊，請參閱 <<c0> [ 關於 SAPDiscoveredObjects.xml 檔案在 SAP 中](../../adapters-and-accelerators/adapter-sap/about-the-sapdiscoveredobjects-xml-file-in-sap.md)。  
  
## <a name="prerequisites"></a>必要條件  
 請確定您選擇要安裝[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]連同[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝。  
  
### <a name="to-connect-to-an-sap-system-using-the-ddex-plug-in"></a>若要連接到 SAP 系統使用的 DDEX 外掛程式  
  
1. 啟動 Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  
  
2. 在 [[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檢視**功能表上，按一下**伺服器總管]**。  
  
3. 在**伺服器總管**，以滑鼠右鍵按一下**資料連接**，然後選取**加入連接**。  
  
4. 在 [**變更資料來源**] 對話方塊中，從**資料來源**方塊中，選取**\<其他\>**。  
  
5. 從**資料提供者**下拉式清單中，選取 **.NET Framework Data Provider for mySAP Business Suite**然後按一下**確定**。 **加入連接**對話方塊隨即開啟。  
  
6. **加入連接**對話方塊會列出不同的連線參數，以連接到 SAP 系統。 一般連接字串來連接到 SAP 系統使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]需要：  
  
   - 輸入連接的連接參數。 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]支援連接類型 A、 B 和 d。若要連接到 SAP 系統必須提供連接參數的任何*一個*一種連線類型。 比方說，針對 A 的連線類型，您必須提供名稱的應用程式伺服器主機和系統編號。  
  
   - 若要連接到 SAP 系統，例如使用者名稱和密碼登入資訊。  
  
     如需有關連接到 SAP 系統使用的連接字串[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱 <<c2> [ 閱讀 SAP 連接字串的資料提供者類型](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md)。  
  
     在 **加入連接**對話方塊方塊中，指定：  
  
   - 任何一種連線類型連線參數。  
  
   - 要連接到 SAP 系統的登入資訊。  
  
   - 是否要啟用 SAP GUI 偵錯。  
  
   - 是否要使用 RFC SDK 追蹤。  
  
     按一下 [確定] 。 下方會建立新的連線節點**資料連接**您在上一個步驟中指定的伺服器名稱的節點。  
  
7. 展開新的連線節點，以檢視**資料表**並**函式模組**節點。  
  
    連線之後下, 圖顯示 [伺服器總管] 中。  
  
    ![DDEX 外掛程式&#45;中的 SAP ADO.NET 提供者](../../adapters-and-accelerators/adapter-sap/media/158afc11-9c90-4333-bc62-5901f8d0c794.gif "158afc11-9c90-4333-bc62-5901f8d0c794")  
  
### <a name="to-add-tables-from-an-sap-system-using-the-ddex-plug-in"></a>若要使用的 DDEX 外掛程式的 SAP 系統從新增資料表  
  
1. 在 **伺服器總管**，以滑鼠右鍵按一下**資料表**節點，然後按一下**搜尋與新增資料表**。  
  
2. 在 **搜尋資料表名稱**文字方塊中，指定搜尋字串以搜尋資料表中的 SAP 系統，然後按一下**搜尋**。  
  
   > [!NOTE]
   >  [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]支援使用只有星號 （*） 萬用字元來搜尋資料表。  
  
3. **搜尋結果**方塊會列出符合搜尋準則的資料表名稱。  
  
    ![DDEX 外掛程式&#45;中搜尋與新增資料表名稱對話方塊](../../adapters-and-accelerators/adapter-sap/media/737fc9c3-5258-4693-a2f3-5b5b8d2483e9.gif "737fc9c3-5258-4693-a2f3-5b5b8d2483e9")  
  
4. 選取對應至您想要新增，然後按一下資料表的核取方塊**新增**。 若要選取所有資料表，請按一下**都全選**。 若要清除所有選取項目，請按一下**全部清除**。  
  
5. 出現對話方塊通知您重新整理後加入的資料表都能看見**資料表**節點。 按一下 [確定] 。  
  
6. 以滑鼠右鍵按一下**資料表**節點，然後選取**重新整理**。 選取的資料表下方**資料表**節點。 按一下 資料表名稱，請參閱中的資料表屬性才能**屬性**窗格。  
  
7. 展開 資料表名稱，才能查看資料表的欄位。 按一下以查看欄位的屬性中的欄位名稱**屬性**窗格。  
  
### <a name="to-add-rfcs-from-an-sap-system-using-the-ddex-plug-in"></a>若要使用的 DDEX 外掛程式的 SAP 系統從新增 Rfc  
  
1. 在 **伺服器總管**，以滑鼠右鍵按一下**函式模組**節點，然後按一下**搜尋與新增函式模組**。  
  
2. 在 **搜尋函式模組**文字方塊中，指定搜尋字串，以在 SAP 系統中，搜尋函式的模組，然後按一下**搜尋**。  
  
   > [!NOTE]
   >  [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]支援使用只有星號 （*） 萬用字元來搜尋功能模組。  
  
3. **搜尋結果**方塊會列出符合搜尋準則的函式模組。  
  
    ![DDEX 外掛程式&#45;中搜尋與新增模組對話方塊](../../adapters-and-accelerators/adapter-sap/media/8c7f9081-80aa-4bfe-8f06-2c751758ddd0.gif "8c7f9081-80aa-4bfe-8f06-2c751758ddd0")  
  
4. 選取對應至函式模組，您想要新增，然後按一下核取方塊**新增**。 若要選取所有模組，請按一下**都全選**。 若要清除所有選取項目，請按一下**全部清除**。  
  
5. 出現對話方塊通知您重新整理後新增的函式模組都能看見**函式模組**節點。 按一下 [確定] 。  
  
6. 以滑鼠右鍵按一下**函式模組**節點，然後選取**重新整理**。 選取的函式模組會出現在之下**函式模組**節點。 按一下函式模組名稱，請參閱中的屬性**屬性**窗格。  
  
7. 展開以查看節點匯入、 匯出、 變更和資料表參數的函式模組名稱。  
  
8. 依序展開**匯入**列出函式模組的匯入參數 節點。 同樣地，依序展開**匯出**並**資料表**節點，以查看函式模組的匯出和資料表參數的清單。  
  
## <a name="see-also"></a>另請參閱  
 [使用 .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)