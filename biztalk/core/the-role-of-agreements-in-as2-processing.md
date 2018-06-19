---
title: 協議的 AS2 處理的角色 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb6a6fe1-8fb4-4998-a1b4-aadad7e672c4
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 712c086cd02eedfd1995e5f378a05d2edd34bb6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279430"
---
# <a name="the-role-of-agreements-in-as2-processing"></a>AS2 處理中協議的角色
組織會使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，從一個或多個交易夥伴接收 AS2 訊息或傳送 AS2 訊息給他們。 交易夥伴，接著定義組織內的商務實體的商務設定檔。 您會在屬於不同交易夥伴的兩個商務設定檔之間的雙向交易夥伴協議內，設定 AS2 屬性。  
  
 您可以在交易夥伴管理 (TPM) 使用者介面中建立交易夥伴協議。 TPM 畫面位於**合作對象**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
 如需有關如何交易夥伴的詳細資訊，請商務設定檔和合約繫結一起放在 TPM 方案，請參閱[交易夥伴管理解決方案的建置組塊](../core/building-blocks-of-a-trading-partner-management-solution.md)。  
  
## <a name="configuring-an-agreement-for-as2-processing"></a>設定協議的 AS2 處理  
 當某個交易夥伴在任何時間從另一個交易夥伴接收 AS2 訊息或傳送 AS2 訊息給另一個交易夥伴時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] AS2 接收管線或 AS2 傳送管線就會根據這兩個交易夥伴之間的 AS2 協議屬性來處理訊息。 您可以設定 AS2 屬性，以便定義 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 如何執行包括輸入和輸出的 AS2 通訊。  
  
> [!NOTE]
>  與 EDI 處理不同的是，當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法判斷協議時，沒有可用的後援 AS2 協議。 只有在判斷協議之後，AS2 接收管線或傳送管線才會處理訊息。  
  
> [!NOTE]
>  AS2 協議會與 EDI 協議分開設定。 當接收文件時，AS2 處理期間會解析 AS2 協議，然後會在 EDI 處理期間個別解析 EDI 協議。 這兩個協議會組成合作關係。 如需詳細資訊，請參閱[交易夥伴協議](../core/trading-partner-agreement.md)。  
  
> [!NOTE]
>  定義合作對象之一般層面 (如名稱與別名、傳送埠和簽章憑證) 的屬性會指定為交易夥伴屬性的一部分。  
  
 HTTP/HTTPS 傳輸可以用於 EDIINT/AS2 編碼訊息或透過 AS2 編碼的非 EDI 訊息。 如果您透過 HTTP/HTTPS 傳輸來傳送 EDIINT/AS2 編碼訊息，則會套用該協議的 EDI 屬性。  
  
 主要組織的簽章憑證中定義**憑證**頁面**BizTalk 群組-群組屬性** 對話方塊。 此外，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可讓您藉由在協議屬性中定義憑證，以覆寫 AS2 訊息的預設簽章憑證。  若要定義特定協議不同的憑證，請使用**簽章憑證**頁面中，單向 AS2 協議**協議屬性** 對話方塊。 如需有關如何指定不同的憑證的指示，請參閱[設定簽章憑證 (AS2)](../core/configuring-signature-certificates-as2.md)。  
  
## <a name="determining-an-agreement-for-as2-processing"></a>判斷協議的 AS2 處理  
 時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]收到 AS2 編碼訊息時，它會嘗試判斷傳送訊息，藉由比對 AS2 合作對象的 as2 標頭-從在單向協議的合作對象的協議設定。 當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送 AS2 編碼訊息時，它會比對合作對象之單向協議內的 AS2-To 標頭與 AS2-To 協議屬性，以嘗試判斷將會接收訊息的合作對象。 如需詳細資訊，請參閱[在內送 AS2 訊息的協議解析](../core/agreement-resolution-for-incoming-as2-messages.md)或[外寄 AS2 訊息的協議解析](../core/agreement-resolution-for-outgoing-as2-messages.md)。  
  
## <a name="see-also"></a>另請參閱  
 [內送 AS2 訊息的協議解析](../core/agreement-resolution-for-incoming-as2-messages.md)   
 [外寄 AS2 訊息的協議解析](../core/agreement-resolution-for-outgoing-as2-messages.md)   
 [設定 AS2 屬性](../core/configuring-as2-properties.md)