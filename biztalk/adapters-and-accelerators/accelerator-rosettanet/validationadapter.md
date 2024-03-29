---
title: ValidationAdapter |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5fe99350-14c0-4ddb-b257-af9a0c4258f6
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbcf26ee8a3a97d2df34bb29dad5d0cf31d4db1a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987903"
---
# <a name="validationadapter"></a>ValidationAdapter
ValidationAdapter 範例會示範如何對回應者公開程序的訊息執行特殊驗證規則。 Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]原生執行驗證，在傳送或接收管線和協調流程中。 如果您想要執行其他驗證，可以建立驗證配接器。 其他驗證可能包含跨欄位或特定業務的驗證規則，而您無法使用 XSD 實作這些規則。  
  
 您可以建立驗證配接器藉由新增[!INCLUDE[btsCSharp](../../includes/btscsharp-md.md)]ValidationAdapter 範例、 發佈介面，並將配接器輸入協議屬性的程式碼。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 接著在訊息處理期間呼叫驗證配接器。  
  
 由於 ValidationAdapter 是由公開程序協調流程使用的，因此，ValidationAdapter 會在與裝載該協調流程之 BizTalk 主控件服務相同的認證下執行。  
  
 ValidationAdapter 範例位於\<*磁碟機*\>: \Program Files\\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\ValidationAdapter。  
  
## <a name="demonstrates"></a>示範  
 ValidationAdapter 範例示範服務內容中電子郵件地址的驗證。 此範例會實作 `IValidateRNIFMessageParts` 介面。 如果電子郵件地址的格式不正確，就會傳回 `RNIFException`。 XML 文件**preambleToValidate**， **serviceHeaderToValidate**， **deliveryHeaderToValidate**，和**serviceContentToValidate**定義的驗證。  
  
 ValidationAdapter 會使用 RNIFerror.IsOkToSendException 屬性，決定在錯誤事件下要傳送的訊息。 如果驗證不成功，ValidationAdapter 便會將 RNIFerror.ErrorCode 設定為非零值。 如果 RNIFerror.IsOkToSendException 屬性為 true，則程序會傳送負值通知。 在 RNIF 2.0 中，這屬於例外狀況訊息。 在 RNIF 1.1 中，則屬於接收通知的例外狀況訊息。 如果 RNIFerror.IsOkToSendException 屬性為 false，並且已設定 0A1，則程序將會傳送 0A1 訊息。 一旦例外狀況訊息、 接收通知的例外狀況訊息或 0A1 訊息，傳送給處理程序，它將會終止。  
  
 如果 RNIFerror.IsOkToSendException 屬性為 false，並且未設定 0A1，則程序將不會傳送例外狀況訊息或 0A1 訊息。 程序會記錄錯誤，然後終止。  
  
 如果驗證成功，ValidationAdapter 便會將 RNIFerror.ErrorCode 設定為 0，並且 BTARN 會將訊息路由傳送至私用程序。 BTARN 只有在驗證成功的情況下，才會將訊息路由傳送至私用程序。  
  
## <a name="to-implement-this-sample"></a>實作這個範例  
 若要實作 ValidationAdapter 範例，您必須在協議中加入驗證配接器。  
  
#### <a name="to-add-the-validation-adapter-to-the-agreement"></a>在協議中加入驗證配接器  
  
1. 按一下 **開始**，指向**所有程式**，指向 Microsoft [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**。  
  
2. 在 [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)]管理主控台中，展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下**協議**。  
  
3. 按兩下您要加入至驗證配接器的協議。  
  
4. 在 **驗證配接器**對話方塊方塊中，按一下省略符號按鈕 (**...**) 按鈕右邊**組件名稱**，移至含有驗證配接器組件的位置，選取適當的.dll 檔案，，然後按一下**開啟**。  
  
5. 按一下向下的箭號**類別名稱**，選取 驗證配接器類別，然後按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)