---
title: 使用商務規則的 3A4 私用回應者協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33d87952-def6-4202-b535-3d80171332eb
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9ca606aa3d8ce6cdb74d4653e910f7db7639ec3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986095"
---
# <a name="3a4-private-responder-orchestration-using-a-business-rule"></a>使用商務規則的 3A4 私用回應者協調流程
PIP3A4PrivateResponder.odx 範例屬於私用程序協調流程，示範如何實作特定夥伴介面程序 (PIP) 的回應者私用程序，以整合商務規則。 如需有關此程序的詳細資訊，請參閱 <<c0> [ 私用的程序協調流程中定義的商務規則](../../adapters-and-accelerators/accelerator-rosettanet/defining-a-business-rule-for-a-private-process-orchestration.md)。  
  
 根據預設，Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]安裝程式安裝中的範例\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\PipAutomation\3A4。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-build-and-initialize-this-sample"></a>若要建置並初始化這個範例  
  
1.  在命令提示字元中，找出*\<磁碟機\>*: files\ Microsoft BizTalk Accelerator for RosettaNet\<版本\>\SDK\PIPAutomation\3A4 資料夾。  
  
2.  執行 Setup.bat 檔案，它會使用 Binding.xml 繫結檔案執行下列動作：  
  
    -   編譯該 Helper 專案，並在全域組件快取中註冊組件。  
  
    -   編譯 PIP3APrivateResponder 專案，並在全域組件快取中註冊組件。  
  
    -   建立 LOB_To_PrivateResponder 接收埠。  
  
    -   建立 LOB_To_PrivateResponder 接收位置。  
  
    -   建立並啟動 PrivateResponder_To_LOB 傳送埠。  
  
    -   編譯並部署 PIP3A4PrivateResponderProcess 協調流程。  
  
    > [!NOTE]
    >  您必須使用 [BizTalk 總管] 完成 PIP3A4PrivateResponderProcess 協調流程的連接埠繫結組態。  
  
    > [!NOTE]
    >  若要復原 setup.bat 所做的變更，請以手動方式取消登錄 PIP3A4PrivateResponder.odx 協調流程、解除部署 Helper 和 PIP3A4PrivateResponder 組件，並且解除部署然後再刪除 samplebtarnpolicy 規則原則。 您無法使用中的 Cleanup.bat *\<磁碟機\>*: files\ Microsoft BizTalk Accelerator for RosettaNet\<版本\>\SDK\PIPAutomation\3A4 資料夾，以復原變更setup.bat 所進行。  
  
## <a name="demonstrates"></a>示範  
 這個範例會訂閱 3A4 要求動作和信號訊息， 並且在 3A4 同步處理和非同步處理程序中都可以運作。 所有其他 PIP 訊息仍會透過一般 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 私用程序路由傳送。 這個範例會叫用「[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 商務規則引擎」，並將內送 3A4 要求訊息傳遞至「規則引擎」。  
  
> [!NOTE]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 提供一個名為中的 samplebtarnpolicy.xml 的範例商務規則原則\<*磁碟機*\>: files\ Microsoft BizTalk Accelerator for RosettaNet\<版本\>\SDK\PipAutomation\3A4。 如需詳細資訊，請參閱 < [BTARN 商務原則範例](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md)。  
  
 若要使用這個範例，請安裝商務規則。 如果訊息符合商務規則，這個程序便會將內送動作訊息儲存在 MessagesToLOB 資料表中，並將 [已傳遞狀態] 設定為 2。 [已傳遞] 資料行值必須為非零，讓商務營運系統應用程式知道它不需要為此要求產生確認。 然後，這個程序會將 3A4 要求訊息對應至 3A4 確認訊息，並使用 `SubmitRNIF` 方法，將回應提交至 MessageStorageIn 資料表。  
  
 如果訊息不符合商務規則，這個程序便會將內送動作訊息儲存在 MessageStorageOut 資料表中，並將 [已傳遞狀態] 設定為 0。  
  
 這個範例包含繫結檔案 (Binding.xml)，讓您可以用來安裝能與 PIP3A4PrivateResponder.odx 協調流程搭配使用的傳送埠 (PrivateResponder_To_LOB)、接收埠 (LOB_To_PrivateResponder) 和接收位置 (LOB_To_PrivateResponder)。 請使用 BTSTask 命令匯入 Binding.xml 檔中的繫結。 如需詳細資訊，請參閱 BizTalk Server 說明中的"< ImportBindings 命令 > 主題。  
  
## <a name="see-also"></a>另請參閱  
 [雙向動作 PIPAutomation 協調流程](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md)   
 [BTARN 商務原則範例](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md)   
 [協調流程範例](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)