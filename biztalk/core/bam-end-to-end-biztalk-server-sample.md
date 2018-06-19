---
title: 在 BizTalk Server 中的 BAM 端對端範例 |Microsoft 文件
description: 如何從使用 「 商務活動監控 BizTalk Server 中的多個元件的事件相互關聯案例
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81406038-7f3f-499f-a003-12423d92c44b
caps.latest.revision: 35
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 117541cdeded0ff6204797f12e6d8cca1afce38b
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26009879"
---
# <a name="bam-end-to-end-biztalk-server-sample"></a>BAM 端對端 (BizTalk Server 範例)
端對端範例會示範如何使用 BAM 來使多個元件 (在此例中是三個協調流程和一個管線) 中的事件相互產生關聯。  
  
 BAM 會重新建構跨越管線元件和協調流程的商務活動。 這適用於以最低層級，藉由呼叫**EventStream.EnableContinuation**從預期有更多活動事件的每個實作元件。 若要呼叫**EnableContinuation**是明確的而 Orchestration1 和 Orchestration2 中會藉由將 Continuation 資料夾加入至一個排程和 ContinuationID 資料夾的排程中的追蹤設定檔的呼叫它。  
  
 下圖說明範例中使用的工作流程。  
  
 ![](../core/media/ebiz-sdk-samples-bam-endtoendwkflw.gif "ebiz_sdk_samples_bam_endtoendwkflw")  

  
## <a name="what-this-sample-does"></a>此範例的用途  
 BAM 端對端範例會示範如何使用 BAM 蒐集一個管線愈多個協調流程的資訊，並更新單一活動。  
  
## <a name="how-this-sample-was-designed-and-why"></a>此範例的設計方式和原因  
 BAM 端對端範例是針對說明下列活動而設計：  
  
-   在管線內使用 BAM。  
  
-   使用追蹤設定檔編輯器 (TPE) 將活動項目對應到協調流程與訊息元素中的圖形。  
  
-   使用接續活動作用中時好解決方案的多個片段提供給活動。  
  

範例的運作方式如下：  
  
1.  輸入的訊息會從*\<範例路徑\>* \BamEndToEnd\Input 資料夾。  
  
2.  管線元件指派唯一的 DocumentID 給訊息，並使用 BAM API 來開始新的 BAM 活動。 DocumentID 會附加當做輸入訊息的個別部分，供協調流程使用。  
  
3.  收到輸入訊息時，就會啟動 Orchestration1 服務。  
  
4.  Orchestration1 修改輸入訊息，並將它當做參數傳遞給 Orchestration2。  
  
5.  Orchestration2 修改輸入的訊息，並將它傳送至 MessageBox 資料庫中，會啟動 Orchestration3。  
  
6.  Orchestration3 修改訊息，並將它寫入至資料夾*\<範例路徑\>* \BamEndToEnd\Output。  
  
7.  每個協調流程更新中的 BAM 活動的活動項目。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 您可以找到此範例位於*\<範例路徑\>* \BAM\BamEndToEnd。  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|----|---|  
|BamEndToEnd.sln|BAM 端對端範例方案。|  
|BamEndToEnd.xls|BAM 定義樣式表。|  
|BamEndToEnd.xml|BAM 定義 XML。|  
|BAMEndToEndBinding.xml|BAM 繫結。|  
|Cleanup.bat|用來解除部署範例的批次檔。|  
|InputMessage.xml|輸入訊息。|  
|Setup.bat|用來編譯和部署範例的批次檔。|  
|\Components\AssemblyInfo.cs|管線元件程式碼。|  
|\Components\BAMMessagePartPLComponent.cs|管線元件程式碼。|  
|\Components\Components.csproj|管線元件專案。|  
|\Messages\InputMessage01.xml<br /><br /> ...<br /><br /> \Messages\InputMessage10.xml|輸入訊息範例。|  
|\Services\BAMInbound.btp|輸入管線檔案。|  
|\Services\BAMPartSchema.xsd|BAM 部分訊息結構描述。|  
|\Services\Orchestration1.odx|協調流程。|  
|\Services\Orchestration2.odx|協調流程。|  
|\Services\Orchestration3.odx|協調流程。|  
|\Services\PropertySchema.xsd|屬性結構描述。|  
|\Services\Schema1.xsd|訊息結構描述。|  
|\Services\Schema2.xsd|訊息結構描述。|  
Services\Schema3.xsd|訊息結構描述。|  
|\Services\Services.btproj|[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk 檔案專案。|  
|\Services\Transform_1.btm|對應檔案。|  
|\Services\Transform_2.btm|對應檔案。|  
|\Services\Transform_3.btm|對應檔案。|  
  
## <a name="how-to-use-this-sample"></a>如何使用此範例  
 若要建置並執行 BAM 端對端範例使用下列程序：  
  
-   [若要建置和初始化此範例](#To_Build_Sample)  
  
-   [若要執行這個範例](#To_Run_Sample)  
  
-   [若要檢視 BAM 資料](#To_View_Data)  
  
##  <a name="To_Build_Sample"></a>建置和初始化此範例  
  
1.  開啟命令提示字元，以系統管理員身分，並執行*\<範例路徑\>* \BAM\BAMEndToEnd\Setup.bat。 Setup.bat 隨即建置及初始化這個範例的 BAM 基礎結構。 保持開啟命令提示字元。  
  
2.  建立將 Orchestration1、 Orchestration2 和 Orchestration3 對應到 BAM 活動的追蹤設定檔。 (詳細的指示建立追蹤設定檔是複雜的程序，因為位於個別的程序呼叫**建立追蹤設定檔**。 此程序會顯示在本文件稍後）。  
  
3.  部署您在上一個步驟中建立的 BamEndToEnd.btt 追蹤設定檔。  在命令提示字元將變更為*\<範例路徑\>* \BAM\BamEndToEnd 目錄。 若要部署追蹤設定檔，輸入下列命令，並按一下**Enter**:  
  
    `“<BizTalkInstallationPath>\Tracking\bttdeploy” BamEndToEnd.btt`
  
     [如何使用 「 追蹤設定檔管理公用程式部署追蹤設定檔](../core/how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility.md)提供詳細資訊。
  
    > [!IMPORTANT]
    >  您可以忽略訊息 ContinuationID Orch1_ 沒有相符的接續。 預期這個訊息，因為在管線元件中，而不是在追蹤設定檔，會定義名為 Orch1_ 接續。  
  
##  <a name="To_Run_Sample"></a>執行這個範例  
  
將檔案複製*\<範例路徑\>* 到資料夾 \BamEndToEnd\InputMessage.xml *\<範例路徑\>* \BamEndToEnd\Input。 幾秒之後，訊息將會消失輸入資料夾中，並輸出訊息出現在*\<範例路徑\>* \BamEndToEnd\Output 資料夾。  
  
##  <a name="To_View_Data"></a>檢視 BAM 資料  
  
1.  開啟 SQL Server Management Studio。  
  
2.  在 SQL Server Management Studio，展開伺服器，展開 **資料庫**，依序展開**BAMPrimaryImport**，然後展開**資料表**。  
  
3.  以滑鼠右鍵按一下**dbo.bam_EndToEndActivity_Completed**，然後按一下 **開啟資料表**。 如果您使用 SQL Server，請按一下**選取前 1000 個資料列**。  
  
     Bam_EndToEndActivity_Completed 資料表的內容會顯示在右窗格中。 資料表中的每個資料列代表 [endtoendactivity] 活動已完成。  
  
#### <a name="rerun-this-sample"></a>重新執行此範例  
  
1.  開啟命令提示字元，以系統管理員身分，並將變更*\<範例路徑\>* \BAM\BamEndToEnd 目錄。 輸入下列命令：  
  
    `“C:\Program Files\Microsoft BizTalk Server <version>\Tracking\bttdeploy” BamEndToEnd.btt /remove`  
  
    > [!NOTE]
    >  如果您未安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]到 C 磁碟機中，您的安裝所在的磁碟機代號取代"C" [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
2.  執行*\<範例路徑\>* \BAM\BAMEndToEnd\Cleanup.bat。 Cleanup.bat 會移除此範例的 BAM 基礎結構。  
  
3.  執行中的步驟**建置和初始化此範例**本主題中的區段。  
  
##  <a name="TPE_procedure"></a>建立追蹤設定檔  
  
1.  按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]。 以滑鼠右鍵按一下**追蹤設定檔編輯器**，和**系統管理員身分執行**。  
  
2.  在左窗格中**追蹤設定檔編輯器**視窗中，按一下 **按一下這裡匯入 BAM 活動定義**。  
  
3.  在**BAM 活動定義名稱**區段**匯入 BAM 活動定義**對話方塊中，選取**endtoendactivity**，然後按一下 **確定**.  
  
4.  在右窗格中**追蹤設定檔編輯器**視窗中，按一下 **按一下這裡選取事件來源**。  
  
5.  在**組件名稱**區段**選取的事件來源父組件**對話方塊中，選取**Microsoft.Samples.BizTalk.BamEndToEnd.Services**，然後按一下**下一步**。  
  
6.  在**協調流程的名稱**區段**選取協調流程**對話方塊中，選取**BamEndToEnd.Services.Orchestration1**，然後按一下  **確定**.  
  
7.  在左窗格中**追蹤設定檔編輯器**視窗中，以滑鼠右鍵按一下**endtoendactivity**，然後按一下 **新 ContinuationID**。 命名新接續識別碼**Orch1_**。 重複此步驟，建立兩個的多個接續識別碼名為**Orch2_** 和**Orch3_**。  
  
8.  以滑鼠右鍵按一下**endtoendactivity**，然後按一下 **新的接續**。 命名新的接續**Orch2_**。 重複此步驟，建立名為另一個接續**Orch3_**。  
  
9. 以滑鼠右鍵按一下 **[receive1]** 圖形，，然後按一下**內容屬性結構描述**。  
  
10. 捲動到結尾**內容屬性名稱**清單，，然後按兩下  **BAMEndToEnd.Services.PropertySchema.DocumentID**。  
  
11. 展開**\<結構描述\>**，然後將拖曳**DocumentID**右窗格中**Orch1_** 的左窗格中。  
  
12. 按一下資料夾圖示的箭號 (![資料夾和向上箭號按鈕](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) 兩次，以顯示協調流程。  
  
13. 拖曳 **[receive1]** 右窗格中的圖形**SBegin1**的左窗格中。  
  
14. 拖曳**StartOrchestration_1**右窗格中的圖形**SEnd1**的左窗格中。  
  
15. 以滑鼠右鍵按一下**StartOrchestration_1**圖形，，然後按一下**訊息內容結構描述**。  
  
16. 按兩下包含值"Message_2"的資料列中**訊息**資料行和值"MessageBody 」 中**一部分**資料行。  
  
     ![顯示訊息 &#95;的 TPE 訊息內容結構描述，則為 2](../core/media/77fbc444-46cf-4d45-8e9c-c330da7ba7d1.gif "77fbc444-46cf-4d45-8e9c-c330da7ba7d1")  
  
17. 展開**Schema2**，然後將拖曳**Data2**右窗格中**Data1**的左窗格中。  
  
18. 按一下**選取事件來源**，然後按一下 **選取內容屬性**。  
  
19. 捲動到結尾**內容屬性名稱**清單，，然後按兩下  **BAMEndToEnd.Services.PropertySchema.DocumentID**。  
  
20. 展開**\<結構描述\>**，然後將拖曳**DocumentID**至**Orch2_** 的左窗格中的接續。  
  
    > [!NOTE]
    >  請勿將 Orch2_ 接續與 Orch2_ 接續識別碼混淆 代表接續識別碼的圖示會包含索引鍵 (![接續識別碼的圖示](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea"))，則代表接續的圖示不含索引鍵 （![接續的圖示](../core/media/test.gif "測試"))。  
  
21. 按一下**選取事件來源**，然後按一下 **選取協調流程排程**。  
  
22. 在**組件名稱**區段**選取的事件來源父組件**對話方塊中，選取**Microsoft.Samples.BizTalk.BamEndToEnd.Services**，然後按一下**下一步**。  
  
23. 在**協調流程的名稱**區段**選取協調流程**對話方塊中，選取**BamEndToEnd.Services.Orchestration2**，然後按一下  **確定**.  
  
24. 以滑鼠右鍵按一下 **[constructmessage_1]** 圖形，，然後按一下**訊息內容結構描述**。  
  
25. 按兩下包含值"Message_3"的資料列中**訊息**資料行和值"BAMPart 」 中**一部分**資料行。  
  
26. 展開**BAMPart**，然後將拖曳**DocumentID**右窗格中**Orch2_** 接續識別碼的左窗格中。  
  
    > [!NOTE]
    >  請勿將 Orch2_ 接續與 Orch2_ 接續識別碼混淆 代表接續識別碼的圖示會包含索引鍵 (![接續識別碼的圖示](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea"))，則代表接續的圖示不含索引鍵 （![接續的圖示](../core/media/test.gif "測試"))。  
  
27. 按一下資料夾圖示的箭號 (![資料夾和向上按鈕 &#45; 箭號](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) 兩次，以顯示協調流程。  
  
28. 拖曳 **[constructmessage_1]** 右窗格中的圖形**SBegin2**的左窗格中。  
  
29. 拖曳 **[send_1]** 右窗格中的圖形**SEnd2**的左窗格中。  
  
30. 以滑鼠右鍵按一下 **[send_1]** 圖形，，然後按一下**訊息內容結構描述**。  
  
31. 按兩下包含值"Message_3"的資料列中**訊息**資料行和值"MessageBody 」 中**一部分**資料行。  
  
32. 展開**Schema3**，然後將拖曳**Data3**右窗格中**Data2**的左窗格中。  
  
33. 從右窗格上方的下拉式清單選取**訊息內容結構描述**。  
  
34. 按兩下包含值"Message_3"的資料列中**訊息**資料行和值"BAMPart 」 中**一部分**資料行。  
  
35. 展開**BAMPart**，然後將拖曳**DocumentID**右窗格中**Orch3_** 的左窗格中的接續。  
  
    > [!NOTE]
    >  請勿將 Orch3_ 接續與 Orch3_ 接續識別碼混淆 代表接續識別碼的圖示會包含索引鍵 (![接續識別碼的圖示](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea"))，則代表接續的圖示不含索引鍵 （![接續的圖示](../core/media/test.gif "測試"))。  
  
36. 按一下**選取事件來源**，然後按一下 **選取協調流程排程**。  
  
37. 在**組件名稱**區段**選取的事件來源父組件**對話方塊中，選取**Microsoft.Samples.BizTalk.BamEndToEnd.Services**，然後按一下**下一步**。  
  
38. 在**協調流程的名稱**區段**選取協調流程**對話方塊中，選取**BamEndToEnd.Services.Orchestration3**，然後按一下  **確定**.  
  
39. 以滑鼠右鍵按一下 **[receive1]** 圖形，，然後按一下**訊息內容結構描述**。  
  
40. 按兩下包含值"Message_3"的資料列中**訊息**資料行和值"BAMPart 」 中**一部分**資料行。  
  
41. 展開**BAMPart**，然後將拖曳**DocumentID**右窗格中**Orch3_** 接續識別碼的左窗格中。  
  
    > [!NOTE]
    >  請勿將 Orch3_ 接續與 Orch3_ 接續識別碼混淆 代表接續識別碼的圖示會包含索引鍵 (![接續識別碼的圖示](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea"))，則代表接續的圖示不含索引鍵 （![接續的圖示](../core/media/test.gif "測試"))。  
  
42. 按一下資料夾圖示的箭號 (![資料夾和向上箭號按鈕](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) 兩次，以顯示協調流程。  
  
43. 拖曳 **[receive1]** 右窗格中的圖形**SBegin3**的左窗格中。  
  
44. 拖曳 **[send_1]** 右窗格中的圖形**SEnd3**的左窗格中。  
  
45. 以滑鼠右鍵按一下 **[send_1]** 圖形，，然後按一下**訊息內容結構描述**。  
  
46. 展開**Schema3**，然後將拖曳**Data3**右窗格中**Data3**的左窗格中。  
  
47. 以滑鼠右鍵按一下**DocumentID**下方**Orch2_** 接續，然後再按一下**設定連接埠對應**。  
  
    > [!NOTE]
    >  請勿將 Orch2_ 接續與 Orch2_ 接續識別碼混淆 代表接續識別碼的圖示會包含索引鍵 (![接續識別碼的圖示](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea"))，則代表接續的圖示不含索引鍵 （![接續的圖示](../core/media/test.gif "測試"))。  
  
48. 在**選取連接埠**區段**選取連接埠**對話方塊中，按一下**BamEndToEnd_ReceivePort**，按一下 較大-符號 ( **>**)，然後按一下 **確定**。  
  
49. 儲存追蹤設定檔來*\<範例路徑\>* \BAM\BamEndToEnd\BamEndToEnd.btt。  
  
## <a name="important-details"></a>重要的詳細資料  
 追蹤設定檔不支援管線。 不過，呼叫**BeginActivity**在管線元件是在協調流程中使用 ActivityID 相同。 若要呼叫**EnableContinuation**與協調流程中使用接續相同。  
  
## <a name="see-also"></a>請參閱  
 [商務活動監控 (BizTalk Server Samples 資料夾)](../core/business-activity-monitoring-biztalk-server-samples-folder.md)