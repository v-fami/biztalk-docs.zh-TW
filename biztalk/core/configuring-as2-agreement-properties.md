---
title: "設定 AS2 協議屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.admin.as2agreement.properties
ms.assetid: a62d8d2a-0b8d-4179-a48f-92f135b5787d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a6f09f85b726869e98712abf354ad3943ce97a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-as2-agreement-properties"></a>設定 AS2 協議屬性
本 節將說明 AS2 傳輸協議屬性 。 在傳輸通訊協定設定當中，您還可以定義訊息是否應該經過簽章、加密等等。  
  
> [!NOTE]
>  設定 AS2 協議是選擇性的動作。 AS2 協議中會定義使用 AS2 通訊協定傳輸訊息的方式。 如果交易夥伴決定使用其他傳輸通訊協定來傳輸訊息，可以選擇不要定義 AS2 協議。 不過，交易夥伴必須定義編碼協議，以控制訊息的構成與編碼方式。 如需編碼協議的詳細資訊，請參閱[設定編碼協議屬性](../core/configuring-encoding-agreement-properties.md)。  
  
> [!IMPORTANT]
>  每次在協議中變更 AS2 設定時，您需要重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主控件執行個體，以便讓變更生效。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [設定一般設定 (AS2)](../core/configuring-general-settings-as2.md)  
  
-   [設定識別項 (AS2)](../core/configuring-identifiers-as2.md)  
  
-   [設定驗證 (AS2)](../core/configuring-validation-as2.md)  
  
-   [設定通知 (MDN) (AS2)](../core/configuring-acknowledgements-mdns-as2.md)  
  
-   [設定本機主機設定 (AS2)](../core/configuring-local-host-settings-as2.md)  
  
-   [設定簽章憑證 (AS2)](../core/configuring-signature-certificates-as2.md)  
  
-   [設定傳送埠關聯 (AS2)](../core/configuring-send-port-association-as2.md)  
  
## <a name="see-also"></a>另請參閱  
 [設定 AS2 屬性](../core/configuring-as2-properties.md)