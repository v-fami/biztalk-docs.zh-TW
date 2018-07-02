---
title: BizTalk Server 執行階段安全性建議 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, runtime
- runtime, security
- discretionary access control lists (DACLs)
- DACLs
- .NET Framework Code Access Security Mechanism
ms.assetid: 1933789d-b79a-47ad-8f70-6f1e99bc2be0
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f929e49a7c7bc94456262ca07a42bfdc02eb1107
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974183"
---
# <a name="biztalk-server-runtime-security-recommendations"></a>BizTalk Server 執行階段安全性建議
您必須將 BizTalk Server 執行階段或引擎安裝在用來接收、傳送、處理和追蹤訊息的所有電腦上。 換句話說，您必須將執行階段元件安裝在建立 BizTalk 主控件執行個體 (處理伺服器) 的電腦上。 建議您依照這些指導方針來保護和部署您作業環境中的 BizTalk Server 執行階段。  
  
- 確定您具有「最小安全性使用者權限」，以便執行 BizTalk 執行階段工作。 如需有關最低安全性使用者權限的詳細資訊，請參閱[最低安全性使用者權限](../core/minimum-security-user-rights.md)。  
  
  > [!NOTE]
  >  BizTalk 組態為這些帳戶提供了執行工作所需的最低權限。  
  
- 每個主控件執行個體的服務帳戶必須具有記錄檔，做為主控件執行個體執行所在的電腦上的服務權限。  
  
- 僅主控件的服務帳戶可以存取與主控件相關的 MessageBox 資料，而且只有這些服務可以公佈到 MessageBox。 若要將資料洩漏攻擊的潛在威脅降到最低，您不應該在多個主控件使用相同的服務帳戶。  
  
- 處理伺服器 (沒有裝載追蹤的主控件) 僅需要連接到 MessageBox 和「管理」資料庫以及主要密碼伺服器。 若是您使用網際網路通訊協定安全性 (IPSec)，則可以限制處理伺服器對這兩個資料庫及主要密碼伺服器的存取權。  
  
- 在相同 BizTalk 主控件內執行的所有元件，都具有與主控件相同的信任層級。 哪些元件應該以相同的主控件執行是由 BizTalk 系統管理員來決定的，因此，這些元件共用相同的信任層級。 BizTalk 確保只有由 BizTalk 系統管理員安裝的組件可以在 BizTalk 主控件中執行。 如果您想要建立進一步限制哪些組件 BizTalk 用途，例如，如果您想要限制 BizTalk 僅執行由特定廠商簽署的組件，或驗證強式名稱簽章，協調流程，您可以使用[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]程式碼存取安全性機制。 如需有關 Microsoft MSDN 網站，在[ http://go.microsoft.com/fwlink/?LinkId=60947 ](http://go.microsoft.com/fwlink/?LinkId=60947)。  
  
- 公佈訊息的授權細項位於 BizTalk 主控件層級。 換言之，若是相同的 BizTalk 主控件內執行了多個協調流程或配接器，則無法限制一個特定協調流程接收傳送到主控件的訊息。  
  
- 未授權主控件接收訊息時，主控件會將訊息放置在它的已擱置佇列中。 依照預設，接收配接器和協調流程在相同的主控件中執行時，協調流程可以讀取主控件的已擱置佇列。 如此一來，協調流程即可拾取 BizTalk 因為授權失敗而擱置的訊息。 因此，建議您不要在相同的主控件中執行協調流程及接收配接器。  
  
- 主控件執行個體是在特定電腦上執行的 Windows 服務。 為了建立主控件執行個體，在想要建立主控件執行個體的電腦上，您必須同時是 BizTalk 系統管理員與 Windows 系統管理員，因為 BizTalk 會建立與主控件執行個體對應的 Windows 服務。  
  
- 當 Microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]產生組件，它會使用產生的整合式開發環境 (IDE) 中的自訂金鑰。 如果您的環境需要您以特定金鑰簽署所有的組件，您必須設定所有的開發電腦使用該金鑰，或使用延遲簽署組件的 IDE...  
  
- 接收和傳送管線中的所有元件都會嘗試保持低記憶體耗用量。 當資料大於特定閾值時，這些元件會將資料傳送到暫存資料夾 (%TEMP%) 的磁碟中。 您必須確保主控件執行個體服務帳戶的暫存資料夾具有適當的判別存取控制清單 (DACL)，如此一來，僅服務帳戶可以讀取這些檔案。 另外也要確定暫存資料夾有足夠的空間，以便未來可以儲存大型檔案。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BizTalk Server 安全性](../core/managing-biztalk-server-security.md)   
 [處理伺服器的連接埠](../core/ports-for-the-processing-servers.md)   
 [BizTalk Server 部署的安全性建議](../core/security-recommendations-for-a-biztalk-server-deployment.md)   
 [安全性規劃](../core/planning-for-security.md)