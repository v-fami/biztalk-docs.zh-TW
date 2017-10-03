---
title: "AS2 在 BizTalk Server 中支援 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8ee230e-8f5f-4b51-99e2-0b38acaf5707
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5e40d7c45ffc8622a420d87bd60e3b74659db93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="as2-support-in-biztalk-server"></a>BizTalk Server 中的 AS2 支援
本主題提供 AS2 處理的簡短一般概觀以及如何[!INCLUDE[prague](../includes/prague-md.md)]實作它。  
  
## <a name="introduction-to-as2"></a>AS2 簡介  
 EDI 所使用的一般傳輸方法是加值型網路 (VAN)。 這類私用網路可提供加值型服務，例如精確與合法的繫結稽核線索。 然而，許多公司是透過網際網路移轉來交換 EDI 文件。 這種做法可降低成本、增加彈性與效率，而且就重複性和擴充性而言也具有優勢。  
  
 透過網際網路傳輸 EDI (EDIINT) 的最常見實作方式，就是使用 AS2 (Applicability Statement 2)。 AS2 規格定義了以 MIME 為基礎的安全點對點商務資料交換。 訊息 (包含具有 MIME 資料的信封) 的傳輸是使用 HTTP over TCP/IP。  
  
 AS2 使用 HTTP POST 作業來傳送 EDI、XML 或其他商務資料。 AS2 並沒有限制為僅傳送 EDI 資料。 Request-URI 會識別用來解開和處理訊息資料的處理程序。 訊息處理通知 (Message Disposition Notification，MDN) 會以通知的形式，透過 HTTP 回應訊息內文傳回，或是透過針對原始傳送者 URL 的新 HTTP POST 作業傳回。  
  
 如需有關 EDI 傳訊的詳細資訊，請參閱[AS2 傳訊](../core/as2-messaging.md)。  
  
## <a name="how-as2-is-implemented-in-biztalk-server"></a>AS2 在 BizTalk Server 中的實作方式  
 [!INCLUDE[prague](../includes/prague-md.md)]包含提供 AS2 支援的原生功能。 這項功能不是產品的增益集 (例如配接器或加速器)， 其已內建在產品中，並且會提供下列功能：  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用 AS2 定義方法來傳送、 接收及驗證訊息。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可協助確保由加密、 簽章和壓縮的資料傳輸的安全性。 若要這樣做，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會使用加密金鑰、 數位簽章和憑證。  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可讓您將內送和外寄 AS2 訊息儲存在不可否認性儲存體。 這包括儲存已編碼或已解碼的 AS2 訊息及儲存 MDN。  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供了可保留附加檔案名稱做為 AS2 訊息的一部分。  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可讓您檢查有重複的內送訊息。  
  
-   您可以在訊息受到通知時，透過相同連線而同步地傳回 MDN，或是透過不同連線而非同步地傳回 MDN。  
  
-   如果指定的時段內未收到 MDN，您可以重新傳送 AS2 訊息。  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供特定的 AS2 狀態報告。 這些報告會提供 AS2 傳輸的完整狀態，其中包括與交換相互關聯的通知。  
  
-   AS2 需要 HTTP 配接器使用接收端和傳送端上。  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可讓您覆寫預設藉由定義每個合約的憑證簽署 AS2 訊息的憑證。 如需如何指定合作對象的不同憑證的指示，請參閱[設定 AS2 屬性](../core/configuring-as2-properties.md)。  
  
## <a name="as2-components-in-biztalk-server"></a>在 BizTalk Server 中的 AS2 元件  
 [!INCLUDE[prague](../includes/prague-md.md)]用於進行 AS2 傳輸的元件包括下列各項：  
  
-   BizTalk EDI 應用程式，其包含處理 AS2 文件時的必要成品 (包括管線、協調流程和結構描述)。  
  
    > [!NOTE]
    >  當您設定中的 AS2 功能[!INCLUDE[prague](../includes/prague-md.md)]，組態程式就會建立此應用程式。 每當建立用於處理 AS2 訊息的應用程式時，您都必須從應用程式中加入 BizTalk EDI 應用程式的參考。 如需詳細資訊，請參閱[如何將參考加入至 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。  
  
-   AS2EdiReceive 管線，其會針對透過 AS2 所接收 EDI 訊息，執行 AS2 處理，然後執行 EDI 處理。 如需詳細資訊，請參閱[AS2 接收元件](../core/as2-receive-components.md)。  
  
-   AS2Receive 管線，其會針對透過 AS2 所接收的非 EDI 訊息，執行 AS2. 處理。 如需詳細資訊，請參閱[AS2 接收元件](../core/as2-receive-components.md)。  
  
-   AS2EdiSend 管線，其會針對透過 AS2 傳送的 EDI 訊息，執行 EDI 處理，然後執行 AS2 處理。 如需詳細資訊，請參閱[AS2 傳送元件](../core/as2-send-components.md)。  
  
-   AS2Send 管線，其會針對透過 AS2 傳送的非 EDI 訊息，執行 AS2 處理。 如需詳細資訊，請參閱[AS2 傳送元件](../core/as2-send-components.md)。  
  
-   交易夥伴管理 (TPM) 使用者介面，可讓您設定的交易夥伴參與 AS2 文件傳輸處理屬性。 如需詳細資訊，請參閱[中協議的角色中的 AS2 處理](../core/the-role-of-agreements-in-as2-processing.md)和**EDI 和 AS2 UI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
-   狀態報告使用者介面，其可提供 AS2 交換的完整狀態及相關通知。 如需詳細資訊，請參閱[EDI 和 AS2 狀態報告](../core/edi-and-as2-status-reporting.md)。  
  
-   移轉工具 (合作對象移轉工具) 可讓您將包含 AS2 屬性的合作對象資料從 BizTalk Server 2006 R2 或 BizTalk Server 2009 移轉至 [!INCLUDE[prague](../includes/prague-md.md)]。 如需詳細資訊，請參閱[移轉 EDI 成品從 BizTalk Server 先前版本](http://msdn.microsoft.com/library/b956a97e-03d0-47ea-a2ce-c07a339c0f2c)。  
  
## <a name="see-also"></a>另請參閱  
 [AS2 方案架構](../core/as2-solution-architecture.md)   
 [EDI 和 AS2 狀態報告](../core/edi-and-as2-status-reporting.md)   
 [開發和設定 BizTalk Server AS2 解決方案](../core/developing-and-configuring-biztalk-server-as2-solutions.md)