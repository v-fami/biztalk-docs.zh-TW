---
title: "開發自訂配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44765fbb-b24d-43b6-a40c-d28e319b90a5
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c13aba7e378d67523ec755837ac65b26989730a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="developing-custom-adapters"></a>開發自訂配接器
為了與外部系統、應用程式和實體交換訊息，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用配接器的概念。 配接器都是 COM 或[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]傳送商務結束訊息的元件。 點 （例如檔案系統、 資料庫和自訂商務應用程式） 使用各種通訊協定。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供支援各種通訊協定的原生配接器。 其中包括：  
  
-   支援從「檔案」位置傳送和接收訊息的 FILE 配接器。  
  
-   適用於 EDI、FTP、HTTP、MSMQ、SMTP、POP3 及 SOAP 通訊協定的配接器  
  
-   適用於 [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] 的配接器  
  
 在某些情況下，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可能需要將訊息傳輸到特定的自訂應用程式，或是使用不存在原生配接器的通訊協定。 有些協力廠商有撰寫配接器以支援其他的通訊協定。 在決定要撰寫自訂配接器之前，您必須判斷是否有適用於通訊協定的配接器。 如需配接器和相關聯的供應商的清單，請參閱[http://go.microsoft.com/fwlink/?LinkId=47140](http://go.microsoft.com/fwlink/?LinkId=47140)。 如果您找不到支援您通訊需求的配接器，即可開發自己的自訂配接器。  
  
 撰寫自訂配接器可能會是具有挑戰性的工作。 為了簡化這項程序，Microsoft 開發了稱為「配接器架構」的基礎。 您可以使用此架構，連同 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SDK 中的範例配接器程式碼，做為開發工作的基礎。  
  
 本節中的主題描述自訂配接器開發秘訣和建議。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [什麼是配接器架構？](../core/what-is-the-adapter-framework.md)  
  
-   [BizTalk Server 如何具現化配接器](../core/how-biztalk-server-instantiates-an-adapter.md)  
  
-   [訊息的批次](../core/message-batches.md)  
  
-   [交易式訊息批次](../core/transactional-message-batches.md)  
  
-   [開發接收配接器](../core/developing-a-receive-adapter.md)  
  
-   [開發傳送配接器](../core/developing-a-send-adapter.md)  
  
-   [具現化的外掛式配接器](../core/instantiating-isolated-adapters.md)  
  
-   [配接器設計問題](../core/adapter-design-issues.md)  
  
-   [配接器如何處理大型訊息](../core/how-adapters-handle-large-messages.md)  
  
-   [如何處理配接器失敗](../core/how-to-handle-adapter-failures.md)  
  
-   [如何終止配接器](../core/how-to-terminate-an-adapter.md)  
  
-   [如何設計高效能的配接器](../core/how-to-design-a-performant-adapter.md)  
  
-   [如何部署自訂的配接器](../core/how-to-deploy-a-custom-adapter.md)  
  
-   [如何測試和偵錯配接器](../core/how-to-test-and-debug-an-adapter.md)  
  
-   [如何將配接器中繼資料新增至 BizTalk 專案](../core/how-to-add-adapter-metadata-to-a-biztalk-project.md)  
  
-   [配接器當地語系化問題。](../core/adapter-localization-issues.md)  
  
-   [設計您的配接器的秘訣](../core/tips-for-designing-your-adapter.md)  
  
-   [配接器設計階段組態](../core/adapter-design-time-configuration.md)  
  
## <a name="see-also"></a>另請參閱  
 [開發自訂元件](../core/developing-custom-components.md)