---
title: 在 BizTalk Server1 的 EDI 支援 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7cddab7a-99ef-4dbb-bb74-9e3d03df3996
caps.latest.revision: 37
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1371d707729c6c0efbc8277dde671d353ab400aa
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979959"
---
# <a name="edi-support-in-biztalk-server"></a>BizTalk Server 中的 EDI 支援
本主題提供 EDI 和 BizTalk Server 如何支援 EDI 的簡短一般概觀。  
  
## <a name="introduction-to-edi"></a>EDI 簡介  
 「電子資料交換」(EDI) 是商業交易夥伴交換 (Exchange) 電子資料時最常使用的方法。 EDI 主要為訊息導向。 文件都會實作為一般檔案，其中可包含批次交易集。 批次交換 (Interchange) 可以包含多個群組，每個群組又可以包含多個交易集或訊息。  
  
 EDI 包含標準組織所制定的特定資料交換 (Interchange) 方法。 主要的 EDI 標準是 X12 (由 ANSI 制定標準，主要用於北美洲) 及 EDIFACT (由聯合國制定標準，主要用於美國境外)。 其他標準都衍伸自這些標準，例如，HIPAA 衍伸自 X12，韓國的 KEDIFACT 衍伸自 EDIFACT。 這些標準在訊息結構和通知結構描述方面近乎相同，卻又有明顯的差異處。  
  
 EDI 標準規定下列項目：  
  
- 文件交換 (Exchange) 中使用的格式、字元集和資料元素。  
  
- EDI 交易中使用的信封  
  
- 確認送達所需的通知  
  
- 提供保證只需一次的傳遞方式，以及自動偵測和報告損毀或不正確的資料。  
  
  雖然 EDI 標準會建立文件結構的規則，但交易夥伴仍需同意要傳輸哪些特定資訊，以及這些資訊的使用方式。 連接兩個交易夥伴之 EDI 系統的設計走向，取決於標準所需的項目，以及交易夥伴達成協議的內容。 如需有關 EDI 傳訊的詳細資訊，請參閱 < [EDI 傳訊](../core/edi-messaging.md)。  
  
> [!NOTE]
>  EDI 訊息與其傳輸不同。 EDI 標準並未規定訊息傳輸，因此 EDI 訊息可透過多種不同方式傳送。  
  
## <a name="how-edi-is-implemented-in-biztalk-server"></a>在 BizTalk Server 中實作 EDI 的方式  
 BizTalk Server 包含可提供 EDI 支援的原生功能。 EDI 是內建在產品中;它不是增益集，例如配接器或加速器一樣。  
  
 **交換處理**  
  
 EDI 功能會在管線中執行下列接收端和傳送端處理，以強制執行 EDI 標準規定的規則。  
  
- 處理內送 EDI 訊息，包括驗證交換 (Interchange) 和產生通知。  
  
- 產生並傳送外寄 EDI 訊息，包括驗證交換 (Interchange) 和根據組態來處理收到的通知。  
  
  **批次處理**  
  
  批次處理作業是由接收管線和協調流程處理：  
  
- 如果收到的批次交換 (Interchange) 需要分割，則 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會將其分割為組成交易集，包括為每個交易集產生 XML 檔案，以及升級產生傳送端批次所需的屬性。  
  
- 如果收到的批次交換 (Interchange) 需要保留，則 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 處理批次時，會保留收到批次時該批次所包含的交易集和群組。  
  
- 如果收到的批次交換 (Interchange) 需要設定，批次會將 EDI 交換集和群組批次收到外寄交換 (Interchange) 中。  
  
- 如有多個合作對象訂閱批次交換 (Interchange)，則 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會傳送批次副本給每個合作對象。  
  
  **交易夥伴協議**  
  
  交易夥伴必須互相定義「交易夥伴協議」，此協議是一組在「BizTalk Server 管理主控台」中定義的屬性。 這些合作對象屬性以及傳送和接收埠/位置屬性，決定接收端與傳送端 EDI 處理方式。 如需有關交易夥伴協議的詳細資訊，請參閱 <<c0> [ 交易夥伴協議](../core/trading-partner-agreement.md)。  
  
  **交換狀態**  
  
  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會提供 EDI 特定狀態報告。 這些狀態報告會提供 EDI 文件交換 (Interchange) 交易的完整狀態，包括與交換 (Interchange) 相互關聯的通知。  
  
## <a name="edi-components-in-biztalk-server"></a>BizTalk Server 中的 EDI 元件  
 Microsoft BizTalk Server EDI 處理所使用的元件包括下列各項：  
  
- 「BizTalk EDI 應用程式」包含處理 EDI 文件所需的成品 (包括管線、協調流程和結構描述)。  
  
  > [!NOTE]
  >  當您在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中設定 EDI 功能時，組態程式就會建立這個應用程式。 每當您建立用於處理 EDI 交換 (Interchange) 的應用程式時，都必須在應用程式中加入「BizTalk EDI 應用程式」的參考。 如需詳細資訊，請參閱 <<c0> [ 如何將參考加入 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。  
  
- 「BizTalk EDI 接收管線」(EdiReceive 管線) 會剖析 EDI 編碼文件、分割 EDI 批次、將 EDI 編碼文件轉換為 XML 編碼、執行 EDI 和 XSD 驗證，以及執行 HIPAA X12 子文件分割作業。 如需詳細資訊，請參閱 < [EDI 接收元件](../core/edi-receive-components.md)。  
  
- 「BizTalk EDI 傳送管線」(EdiSend 管線) 則會將 XML 文件轉換為 X12 或 EDIFACT 編碼、序列化 EDI 編碼文件，以及執行 EDI 和 XSD 驗證。 如需詳細資訊，請參閱 < [EDI 傳送元件](../core/edi-send-components.md)。  
  
- 交易夥伴管理 (TPM) 使用者介面可讓您設定參與 EDI 文件交換與 AS2 文件傳輸之交易夥伴的處理屬性。 如需詳細資訊，請參閱 <<c0> [ 中協議的角色中處理 EDI](../core/the-role-of-agreements-in-edi-processing.md)並**EDI 和 AS2 UI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
- 批次處理協調流程會將 EDI 交換 (Interchange) 進行批次處理，並設定批次交換 (Interchange) 傳送的內容屬性。 路由協調流程則會處理訊息符合多個批次的情況，並建立該訊息的必要副本數目。 如需詳細資訊，請參閱 <<c0> [ 處理內送批次](../core/processing-incoming-batches.md)並[批次處理外寄 EDI 訊息](../core/batching-outgoing-edi-messages.md)。  
  
- 狀態報告使用者介面可提供 EDI 交換 (Interchange) 的完整狀態及相互關聯的通知。 如需詳細資訊，請參閱 < [EDI 和 AS2 狀態報告](../core/edi-and-as2-status-reporting.md)。  
  
- Visual Studio 中的設計階段工具可讓您產生執行個體、驗證執行個體、驗證結構描述、測試對應以及驗證對應。 如需詳細資訊，請參閱 <<c0> [ 使用的設計階段 XML 工具](../core/using-design-time-xml-tools.md)。  
  
- 結構描述儲存機制包括 X12、EDIFACT、HIPAA X12N 4010A XSD、EANCOM 和控制結構描述。 如需詳細資訊，請參閱 < [EDI 文件結構描述支援](../core/edi-document-schema-support.md)。  
  
- 移轉工具 （合作對象移轉工具） 可讓您將 EDI 合作對象資料從 BizTalk Server 2006 R2 或 BizTalk Server 2009 移轉至 BizTalk Server。 如需詳細資訊，請參閱 <<c0> [ 移轉 EDI 成品從 BizTalk Server 先前版本](http://msdn.microsoft.com/library/b956a97e-03d0-47ea-a2ce-c07a339c0f2c)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 中的 EDI 處理](../core/edi-processing-in-biztalk-server.md)   
 [BizTalk Server 中的 HIPAA 支援](../core/hipaa-support-in-biztalk-server.md)   
 [EDI 支援問題](../core/edi-support-issues.md)   
 [EDI 解決方案架構](../core/edi-solution-architecture.md)   
 [EDI 和 AS2 狀態報告](../core/edi-and-as2-status-reporting.md)   
 [開發和設定 BizTalk Server EDI 解決方案](../core/developing-and-configuring-biztalk-server-edi-solutions.md)