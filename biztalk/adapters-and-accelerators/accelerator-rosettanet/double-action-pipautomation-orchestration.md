---
title: 雙向動作 PIPAutomation 協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9159f7b1-cb83-41f1-8637-39c5ddcc63ae
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f04b04d20189307c3d42e60c43c2c4c9254ffb7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008423"
---
# <a name="double-action-pipautomation-orchestration"></a>雙向動作 PIPAutomation 協調流程
DoubleAction.odx 範例顯示如何實作協調流程，自動為雙向動作「夥伴介面程序 (PIP)」0C2、0C4、3A2 和 3A4 產生回應。 您可以擴充此範例專案來支援其他的雙向動作 PIP。  
  
> [!NOTE]
>  在範例資料夾中的對應是範例。 您必須根據特定的需求，對這些對應進行變更後，才能加以使用。  
  
> [!NOTE]
>  您應該擴充這個範例專案，使其僅支援雙向動作 PIP，而非單向動作 PIP。 如果將它擴充為處理單向動作 PIP，這個協調流程將會傳回錯誤。 若要確認這個協調流程將不會處理單向動作 PIP，請參閱下面的「篩選單向動作訊息」部分。  
  
 根據預設，Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]安裝程式安裝在此範例\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for rosettanet\sdk\pipautomation\doubleaction。  
  
 這個範例專案包括：  
  
- 預存程序 (`PipAutomationGetAction)`擷取新動作訊息 Pip 0c2、 0c4、 3A2 和 3A4。  
  
- 繫結至 SQL 預存程序的接收位置 (MessagesToLOB_Receive_Location)。  
  
- 處理每個 PIP、根據每個 PIP 的對應產生適當的回應，以及將回應儲存在 BTARNDATA 資料庫之 MessagesFromLOB 資料表中的協調流程。 協調流程會使用來自 Microsoft.Solutions.BTARN.Shared.dll 的 `RNIFSubmit` 方法來提交訊息。  
  
- Setup.bat 檔用來建立 MessagesToLOB_Receive_Port (與 DoubleAction 協調流程搭配使用) 的繫結檔案 (DoubleActionBinding.xml)。  
  
- 用於建置及初始化範例的安裝程式檔案。 如果 BizTalk Server 正在執行的 32 位元電腦上，請在中執行檔案 setup.bat\<磁碟機\>: \Program Files\Microsoft BizTalk Accelerator for RosettaNet \SDK\PIPAutomation\DoubleAction 資料夾。 如果 BizTalk Server 正在執行的 64 位元電腦上，執行相同的資料夾中的 setupx64.bat。  
  
  協調流程會使用 BTARNData 資料庫 (來源檔案是 DoubleAction 目錄中的 DoubleAction.sql 檔) 中的 PipAutomationGetAction 預存程序，接收訊息。 這個預存程序會接收來自 MessagesToLOB 資料表的訊息。  
  
  若要擴充這個範例專案，使其支援其他的雙向動作 PIP，請在協調流程中，為該雙向動作 PIP 加入路徑。 這個路徑必須包含將把回應訊息建構為要求訊息的對應。 例如，請參閱 < [3A2 要求至 3A2 回應的對應範例](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md)並[3A4 要求至 3A4 回應的對應範例&#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md)。  
  
### <a name="to-build-and-initialize-this-sample"></a>若要建置並初始化這個範例  
  
1. 在命令提示字元中，找出*\<磁碟機\>*: \Program Files\Microsoft BizTalk Accelerator for RosettaNet\SDK\PIPAutomation\DoubleAction 資料夾。  
  
   > [!NOTE]
   >  執行安裝程式前，在 [記事本] 中開啟 DoubleAction.sql 檔案 (在上述資料夾中)。 在 **檔案**功能表上，按一下**另存新檔**。 在  **Encoding**清單中，選取**ANSI**，然後按一下 **儲存**。 按一下 **是**覆寫現有的檔案。  
  
2. 如果您的 BizTalk Server 正在執行的 32 位元電腦上，請在中執行檔案 setup.bat\<磁碟機\>: \Program Files\Microsoft BizTalk Accelerator for RosettaNet\SDK\PIPAutomation\DoubleAction 資料夾。 如果您的 BizTalk Server 安裝正在執行的 64 位元電腦上，執行相同的資料夾中的 setupx64.bat。 這個批次檔將會執行下列動作：  
  
   - 在 BTARNDATA 資料庫中建立 SQL 預存程序 (`PipAutomationGetAction`)，以便從 MessagesToLOB 資料表擷取動作訊息。 這也能確保所擷取的記錄將不會再遭到讀取。  
  
   - 編譯 HeaderHelper [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] 專案，並在全域組件快取中註冊組件。  
  
   - 建立並繫結 BizTalk Server SQL 接收埠 (MessagesToLOB_Receive_Port)。  
  
   - 啟用接收位置 (MessagesToLOB_Receive_Location)。  
  
   - 編譯及部署雙向動作 PIPAutomation 協調流程 (DoubleAction.odx)。  
  
   - 繫結和啟動 BizTalk Server 協調流程。  
  
     > [!NOTE]
     >  範例在編譯時會出現一些警告。 您可以忽略這些警告。  
  
     > [!NOTE]
     >  此範例會使用預設的主機名稱**BizTalkServerApplication**部署專案時。 如果您想要不同的主控件下執行這個範例中，您必須編輯位於下 DoubleActionBinding.xml 的預設主機名稱\<SDK\>\PIPAutomation\DoubleAction 資料夾。  
  
### <a name="to-run-the-double-action-pipautomation-sample"></a>執行雙向動作 PIPAutomation 範例  
  
1. 建立主要角色為啟動者的 3A4 協議。 將主要組織的 GBI 設為 123456789，並將夥伴組織的 GBI 設為 987654321。 這會讓您使用 SDK 的 SampleInstances 資料夾之 LOBApplication 資料夾底下提供的範例。  
  
2. 使用「回送」鏡像協議公用程式，為步驟 1 所建立的 3A4 PIP 建立鏡像。  
  
3. 使用 LOBApplication.exe SDK 公用程式，提交「3A4 PIP 要求」訊息。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 資料夾中包含了輸入的範例\<*安裝目錄*\>\SDK\LOBApplication\SampleInstances\3A4_Request.xml。  
  
4. 在 BTARNDATA 資料庫上執行下列查詢：  
  
   ```  
   Select * from MessagesToLOB  
   ```  
  
5. 經過數秒後，資料表中會出現四個訊息。 其中兩個是確認信號。 一個是「非同步 3A4 要求訊息」。 另一個則是「非同步 3A4 回應訊息」。  
  
   > [!NOTE]
   >  若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。 您必須先執行 Cleanup.bat，才能再度執行 Setup.bat。  
  
## <a name="remarks"></a>備註  
 公用協調流程會自動產生確認訊息 (ACK 和 NACK 信號訊息)。 商務營運系統 (LOB) 應用程式則不需要產生這些訊息。  
  
 這種路由至 MessagesFromLOB 資料表的訊息格式，稱為 LOBMessage。 結構描述位於 C:\Program Files\Microsoft BizTalk Accelerator for RosettaNet\SDK\RNIFSchemas\GlobalSchemas\LOBMessage.xsd。 如果您使用 `RNIFSubmit` 方法，則不需要處理訊息格式。 您只需要提交具有其他資訊的 ServiceContent。 `RNIFSubmit` 會將記錄填入 MessagesFromLOB 資料表中。  
  
## <a name="filtering-out-single-action-messages"></a>篩選單向動作訊息  
 這個協調流程應該只會接收雙向動作訊息。 您不應該擴充此範例專案來支援單向動作 PIP。 如果您使用這個協調流程處理單向動作訊息，BTARN 將會回報錯誤。 為了避免協調流程接收單向動作訊息，請變更下列 PIPAutomationGetAction 預存程序中的程式碼行：  
  
```  
SELECT PIPInstanceID,DestinationPartyName,SourcePartyName,PIPCode,PIPVersion,ServiceContent FROM MessagesToLOB  
```  
  
 在上述程式碼行中，加入將會篩選出單向動作訊息的 WHERE 子句。 將所有您要處理的單向動作訊息包含在 WHERE 子句中。 這個程式碼行看起來應該如下：  
  
```  
SELECT PIPInstanceID,DestinationPartyName,SourcePartyName,PIPCode,PIPVersion,ServiceContent FROM MessagesToLOB WHERE PIPCode NOT IN ( '0A1', '3B2', '3C3', '0C1', '0C3' )  
```  
  
## <a name="see-also"></a>另請參閱  
 [3A2 要求至 3A2 回應的對應範例](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md)   
 [3A4 要求至 3A4 回應的對應範例](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md)   
 [協調流程範例](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)