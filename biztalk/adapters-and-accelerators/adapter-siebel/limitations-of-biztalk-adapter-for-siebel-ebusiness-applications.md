---
title: BizTalk Adapter for Siebel eBusiness 應用程式的限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- limitations of, Siebel adapter
- Siebel adapter, limitations of
ms.assetid: fda63dd6-bad5-4f6d-8cc1-5855efb6f063
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e47e558ccf0d9841c47911490c1cee319515fd90
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019442"
---
# <a name="limitations-of-biztalk-adapter-for-siebel-ebusiness-applications"></a>BizTalk Adapter for Siebel eBusiness 應用程式的限制
下列已知的限制[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]:  
  
- [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不是搭配 Microsoft BizTalk Adapter for Siebel eBusiness 應用程式，配接器的舊版相容。 配接器的目前版本不支援傳送和接收有使用舊版配接器所產生的結構描述的訊息。  
  
  > [!NOTE]
  >  您可以修改 BizTalk 專案的舊版 Siebel 配接器，以使用新的 WCF 式[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 移轉 BizTalk 專案建立使用 Siebel 配接器的上一個版本](http://msdn.microsoft.com/library/ae61d3df-c5ca-4891-86b1-9f0dd6d3a59e)。  
  
- [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不支援工作流程物件。  
  
- [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不會驗證在其中用戶端，請傳遞 Siebel 系統的時間值的格式。 配接器用戶端必須先確定指定的日期和時間欄位的值會遵守 Siebel 系統所預期的格式。  
  
- [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不會執行結構描述驗證。 比方說，長度為 30 的欄位可以接受與長度 100 的值，如果允許 Siebel 系統。 因為用戶端會透過商務物件插入的資料不一定會實際寫入至資料庫的資料也可能導致在某些情況下的資料遺失。 配接器用戶端必須明確驗證針對呈現的配接器的結構描述的輸入。 不過，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會驗證所有必要的欄位 （適用於商務元件），或未指定引數 （適用於商務服務）。  
  
- [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]預期在標準的 Siebel 格式中指定的時間值 — 也就是 hh: mm:。 時間值中指定的任何其他格式都會產生錯誤，而[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會擲回`TargetSystemException`。  
  
- 在某些情況下，Siebel 應用程式可能會或可能不會擲回的錯誤訊息。 例如，搜尋作業使用運算式可能會擲回例外狀況或傳回零 accords。 因此，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可能會擲回`TargetSystemException`或取得空的 XML，做為輸出。  
  
- 來自 Siebel 系統使用 WCF 服務模型中，擷取資料時[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不會還原序列化 Xml 具有超過 65536 的節點。 請確定輸出 XML 節點小於或等於為 65536。 您可以修改您的應用程式的 app.config 檔，以解決這項限制。 如需相關指示，請參閱 < [Siebel 配接器的疑難排解操作問題](../../adapters-and-accelerators/adapter-siebel/troubleshoot-operational-issues-with-the-siebel-adapter.md)。  
  
- [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]商務元件圖層，而不是資料庫層級中擷取欄位的最大長度。 因此，如果您嘗試要插入的值符合資料庫資料行的最大長度，但會大於商務元件的對應欄位的最大長度，此值寫入資料庫可能會不同於您想要的值若要輸入。  
  
- 在執行批次作業 （Insert、 Update 和 Delete） 時[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]擲回錯誤，如果第一項作業會導致錯誤。 不過，如果第一個作業成功，而且任何後續的作業失敗，配接器不會擲回錯誤，但而在輸出中的成功作業會傳回對應的記錄識別碼。 配接器用戶端必須明確確認所有作業是否都已成功。  
  
- 因為基礎 Siebel 用戶端 API，逾時處理的問題而[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不支援命令，並連接逾時。  
  
- 假設使用者"A"在 Siebel 中產生作業的中繼資料的位置。 另一位使用者"B"，具有較低的權限，比"A，"使用者將能夠存取的中繼資料。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不會執行任何檢查，以驗證是否"B"的使用者必須取得中繼資料的存取。 不過，由於權限不足，"B"的使用者可能無法執行 Siebel 系統的任何作業使用的中繼資料。  
  
- [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不支援指定的連線有任何參數值的特殊字元的 URI。 每個參數值包含特殊字元，請確定您的特殊字元取代對應的值，所指定的 URI 編碼標準。  
  
- 使用與介面卡時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，如果您的認證，在 WCF 自訂傳送連接埠不正確，不會處理要求訊息。 您指定正確的認證之後，訊息傳送至 Siebel 系統中，並在收到回應。 不過，回應訊息不適用於輸出連接埠。 在此情況下，您可能需要重新啟動主控件執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [了解 BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md)