---
title: "ApplicationAdapter |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f9b876b-cd37-4e24-a476-186adc155ac0
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc2808f8cdc2d24a2f7c13864a153361984d0981
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="applicationadapter"></a>ApplicationAdapter
ApplicationAdapter 範例會示範當您收到訊息時，如何從公開程序和私用程序 (回應者或啟動者) 傳送通知。 您可以利用想要的任何其他功能自訂這個範例。  
  
 ApplicationAdapter 範例會示範如何實作 `IApplicationAdapter` 類別的 `ApplicationAdapter1` 介面。 這個類別包含 `BeginNotify` 和 `Notify` 這兩個方法。 每個類別的參數都是訊息類別、來源合作對象名稱、目的合作對象名稱、夥伴介面程序 (PIP) 代碼、PIP 執行個體識別碼以及 PIP 版本。  
  
 輸入組件名稱和類別名稱設定協議的 ApplicationAdapter**一般** 索引標籤中，協議[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] ([!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]) 管理主控台。 應用程式配接器 .dll 檔會在與 BizTalk 主控件服務相同的認證下執行。  
  
 如果您變更 ApplicationAdapter 範例或 ApplicationAdapter 範例所依賴的任何外部環境變數，則必須重新啟動裝載 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 公開程序的 BizTalk 主控件服務。  
  
 ApplicationAdapter 範例程式碼位於\<*磁碟機*>: files\ BizTalk\<版本 > Accelerator for RosettaNet\SDK\ApplicationAdapter\\。  
  
## <a name="demonstrates"></a>示範  
 ApplicationAdapter 範例會示範如何通知回應者私用程序，公開程序已經收到訊息。 通知會指示訊息類別、來源合作對象名稱、目的合作對象名稱、PIP 代碼、PIP 版本以及 PIP 執行個體識別碼。 您可以對動作或回應訊息傳送這個通知。  
  
 `BeginNotify` 和 `Notify` 方法的運作方式如下：  
  
1.  回應者公開程序會接收訊息。  
  
    > [!NOTE]
    >  下列步驟也適用於公開啟動者從回應者接收回應訊息的情況。  
  
2.  如果接收管線、公開程序和驗證配接器 (如果適用) 執行的驗證成功，回應者公開程序就會呼叫 `BeginNotify` 類別中的 `ApplicationAdapter` 方法。 這個方法會通知回應者私用程序，公開程序已經收到新的訊息，並將訊息儲存在 MessageBox 資料庫中。  
  
3.  回應者公開程序會傳送信號訊息給啟動者。  
  
4.  回應者公開程序會傳送訊息服務內容給回應者私用程序。  
  
5.  回應者私用程序會將訊息放在 BTARNDATA 資料庫的 MessagesToLOB 表格中。  
  
6.  回應者私用程序會呼叫 `Notify` 類別中的 `ApplicationAdapter` 方法，將 End Notify 訊息傳回給回應者公開程序。 回應者公開程序必須接收這個 End Notify 訊息，程序才能順利完成。 否則，訊息會處於擱置狀態。  
  
> [!NOTE]
>  您可以使用 `Notify` 訊息發出信號，告知企業營運系統 (LOB) 應用程式，此訊息正在 MessagesToLOB 表格中等候。 只要系統通知 LOB 應用程式，LOB 應用程式就能從該表格接收訊息。  
  
## <a name="to-implement-this-sample"></a>實作這個範例  
 若要實作 ApplicationAdapter 範例，您必須在協議中加入應用程式配接器。  
  
#### <a name="to-add-the-application-adapter-to-an-agreement"></a>在協議中加入應用程式配接器  
  
1.  按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] **BizTalk\<版本 > Accelerator for RosettaNet**，然後按一下  [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]**管理主控台**。  
  
2.  在[!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)]管理主控台中，展開  [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下**協議**。  
  
3.  按兩下您要加入至應用程式配接器的協議。  
  
4.  在**應用程式配接器**方塊中，按一下省略符號按鈕 (**...**) 右邊的按鈕**組件名稱**，移至包含應用程式配接器組件的位置、 選取適當的.dll 檔案，然後按一下**開啟**。  
  
5.  按一下向下的箭號**類別名稱**，選取 應用程式配接器類別，然後按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)