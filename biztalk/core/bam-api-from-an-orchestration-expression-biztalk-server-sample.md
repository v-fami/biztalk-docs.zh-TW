---
title: BAM API 範例協調流程運算式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 341bc333-9bfc-484c-b431-9a71f9188792
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5413940eaba97e6f68d5e068e26625f320e6e817
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
ms.locfileid: "29710981"
---
# <a name="bam-api-from-an-orchestration-expression-biztalk-server-sample"></a>BAM API，從協調流程運算式 （BizTalk Server 範例）
這個範例會示範如何︰  
  
-   使用 BAM API，從 BizTalk Server 協調流程運算式。  
  
-   重複訊息內的項目，做為個別的活動執行個體的追蹤。  
  
-   建立追蹤使用追蹤設定檔的 BAM 資料之間的關聯性，並使用 BAM API 追蹤 BAM 資料。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 您可以找到此範例位於*\<範例路徑\>* \BAM\BamFromExpression。  
  
 下表列出此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|----------|-----------------|  
|BamDefinition.xls|BAM 定義樣式表。|  
|BamDefinition.xml|BAM 定義。|  
|BamFromExpression.btproj|追蹤檔案的專案的 visual Studio。|  
|BamFromExpression.sln|Visual Studio 方案。|  
|Cleanup.bat|用來解除部署範例的批次檔。|  
|InputMessage.xml|輸入訊息。|  
|Orchestration1.odx|協調流程。|  
|PoSchema.xsd|訂單結構描述。|  
|PropertySchema.xsd|屬性結構描述。|  
|Setup.bat|用來編譯和部署範例的批次檔。|  
|QueryBam.sql|SQL 指令碼。|  
  
## <a name="create-the-tracking-profile"></a>建立追蹤設定檔  
  
1.  開啟命令提示字元，以系統管理員身分，並執行*\<範例路徑\>* \BAM\BAMFromExpression\Setup.bat。 Setup.bat 會初始化 BAM 基礎結構，此範例中，並部署 BAM 活動。  
  
2.  從您**程式** > **Microsoft BizTalk Server**，以滑鼠右鍵按一下**追蹤設定檔編輯器**，和**系統管理員身分執行**.
  
3.  在左窗格中 **追蹤設定檔編輯器** ] 視窗中，按一下 [ **按一下這裡匯入 BAM 活動定義**。  
  
4.  在 **BAM 活動定義名稱** 區段 **匯入 BAM 活動定義** 對話方塊中，選取 **FromExpressionPo**, ，然後按一下  **確定**。  
  
5.  在右窗格中 **追蹤設定檔編輯器** ] 視窗中，按一下 [ **按一下這裡選取事件來源**。  
  
6.  在 **組件名稱** 區段 **選取的事件來源父組件** 對話方塊中，選取 **Microsoft.Samples.BizTalk.BamFromExpression**, ，然後按一下  **下一步**。  
  
7.  在 **協調流程名稱** 區段 **選取協調流程** 對話方塊中，選取 **BamFromExpression.Orchestration1**, ，然後按一下  **確定**。  
  
8.  以滑鼠右鍵按一下 **Receive_1** 圖形，，然後按一下 **訊息內容結構描述**。  
  
9. 展開**\<結構描述\>**，依序展開**PurchaseOrder**，依序展開**從**，然後將拖曳**PoID**方窗格**ActivityID**的左窗格中。  
  
10. 從右窗格中，將下列項目並放在左窗格中的具名節點︰  
  
    |來源|若要|  
    |----------|--------|  
    |名稱|來源|  
    |State|State|  
    |City|City|  
    |Phone|Phone|  
    |Total|PoTotal|  
  
11. 按一下資料夾圖示的箭號 (![資料夾和向上按鈕 &#45; 箭號](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) 以顯示協調流程。  
  
12. 拖放到 **Receive_1** 在右窗格中的圖形 **Received** 的左窗格中。  
  
13. 拖放到 **Send_1** 在右窗格中的圖形 **傳送** 的左窗格中。  
  
14. 儲存追蹤設定檔來*\<範例路徑\>* \BAM\BamFromExpression\ BamFromExpression.btt。  
  
15. 在 **工具** ] 功能表上，按一下 [ **套用追蹤設定檔**。  
  
## <a name="build-and-initialize-this-sample"></a>建置和初始化此範例  
  
部署追蹤設定檔 BamFromExpression.btt。 請參閱[如何部署追蹤設定檔與追蹤設定檔管理公用程式](../core/how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility.md)。  
  
## <a name="run-this-sample"></a>執行這個範例  
  
將檔案複製*\<範例路徑\>* 至 \BamFromExpression\InputMessage.xml *\<範例路徑\>* \BamFromExpression\Input。  
  
在 10 秒內的輸出訊息會出現在*\<範例路徑\>* \BamFromExpression\Output。  
  
## <a name="view-the-bam-data"></a>檢視 BAM 資料  
  
1.  開啟 SQL Server Management Studio。  
  
2.  在 SQL Server Management Studio 中，展開伺服器，展開 **資料庫**, ，依序展開 **BAMPrimaryImport**, ，然後展開 **資料表**。  
  
3.  以滑鼠右鍵按一下 **dbo.bam_fromexpressionpo_completed**, ，然後按一下  **開啟資料表**。 如果您使用 SQL Server，請按一下**選取前 1000 個資料列**。  
  
     bam_FromExpressionPo_Completed 資料表的內容會顯示在右窗格中。 有一個資料列 (活動識別碼為 123) 代表輸入訊息中所含價值 $345 的訂單。  
  
4.  以滑鼠右鍵按一下 **dbo.bam_FromExpressionPoItem_Completed**, ，然後按一下  **開啟資料表**。 如果您使用 SQL Server，請按一下**選取前 1000 個資料列**。  
  
     Bam_FromExpressionPoItem_Completed 資料表的內容會顯示在右窗格中。 兩個資料列有活動識別碼 123_0 和 123_1，代表訂單中的項目︰ Flash MC 和紅外線解碼器。  
  
5.  以滑鼠右鍵按一下 **dbo.bam_FromExpressionPoItem_CompletedRelationships**, ，然後按一下  **開啟資料表**。 如果您使用 SQL Server，請按一下**選取前 1000 個資料列**。  
  
     Bam_FromExpressionPoItem_CompletedRelationships 資料表的內容會顯示在右窗格中。 資料表中的每個資料列都代表 FromExpressionPoItem 活動與 FromExpressionPo 活動之間的關聯性。 中的值 **ActivityID** FromExpressionPoItem 活動的活動識別碼是指資料行。 中的值 **ReferenceData** FromExpressionPo 活動的活動識別碼是指資料行。 在此情況下，兩個記錄會指出 Flash MC 和紅外線解碼器項目是 $345 的訂單與相關聯。  
  
## <a name="re-run-the-sample"></a>重新執行範例  
  
1.  開啟命令提示字元，以系統管理員身分，並執行*\<範例路徑\>* \BAM\BamFromExpression\Cleanup.bat 移除追蹤設定檔和其他 BAM 基礎結構。 
  
2.  執行*\<範例路徑\>* \BAM\BamFromExpression\Setup.bat 編譯範例，並將它部署。  
  
## <a name="see-also"></a>另請參閱  
 [商務活動監控 （BizTalk Server 範例資料夾）](../core/business-activity-monitoring-biztalk-server-samples-folder.md)   
 [活動關係](../core/activity-relationships.md)