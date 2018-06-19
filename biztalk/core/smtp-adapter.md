---
title: SMTP 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SMTP adapters, about SMTP adapters
- SMTP adapters, authenticating
- send adapters, SMTP adapters
- authenticating, SMTP adapters
- SMTP adapters
- SMTP adapters, send adapters
ms.assetid: b712f76d-3ce4-4780-9627-951e5951bd8a
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0d0d16bf266d0b636aa9955b5c25b37d9ab54d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277598"
---
# <a name="smtp-adapter"></a>SMTP 配接器
您可以使用「簡易郵件傳送通訊協定」(SMTP) 配接器在執行 Microsoft BizTalk Server 的伺服器和其他應用程式之間，利用 SMTP 通訊協定的方式來交換資訊。 BizTalk Server 可建立電子郵件訊息並將它傳送到指定的電子郵件地址，將訊息傳送到其他應用程式。 SMTP 傳送配接器會在內部建立一個以 SMTP 為基礎的電子郵件訊息，並將訊息傳送到目標電子郵件地址。 目標電子郵件地址是 SMTP 配接器的一個屬性。 當您設定 SMTP 傳送埠時，「BizTalk 總管」會公開這個屬性。  
  
 SMTP 配接器支援在中的使用萬用字元**TO**， **FROM**， **CC**和**主旨**屬性，並將它們解析為其實際值。 中的萬用字元**TO**， **FROM**，和**CC**屬性無法解決，SMTP 傳輸會記錄錯誤，並將訊息放入擱置的佇列或將訊息重新導向至備份傳輸。 如果無法解析萬用字元**主旨**屬性，將訊息傳送與**主旨**屬性所指定完全相同的屬性 （例如，"訊息 %messageid%")。  
  
 依照預設，SMTP 訊息的訊息文字是純文字。 若要在訊息內文中使用 HTML，您可以設定配接器在訊息文字使用 HTML 檔案的內容。  
  
 如需有關 SMTP 安全性問題的詳細資訊，請參閱[SMTP 配接器安全性建議](../core/smtp-adapter-security-recommendations.md)。  
  
 SMTP 配接器僅由一個配接器和一個傳送配接器組成。 傳送配接器控制使用 SMTP 配接器的傳送埠。  
  
 本主題討論通過 SMTP 傳送埠配接器的訊息流程。  
  
 **SMTP 傳送配接器**  
  
 SMTP 傳送配接器從伺服器取得訊息，然後將它們公佈到 SMTP 伺服器，該伺服器會將訊息傳送給電子郵件收件者。 SMTP 傳送配接器從 BizTalk 訊息物件的內文部分、從指定的檔案，或從設定配接器時可用的對話方塊中所輸入的文字，取得訊息內容。  
  
 在 SMTP 傳送配接器成功將訊息公佈到 SMTP 伺服器之後，SMTP 傳送配接器會從 MessageBox 資料庫刪除訊息。  
  
 SMTP 傳送配接器可以要求傳遞通知，並讀取透過 SMTP 傳送配接器傳送的訊息回條。 SMTP 配接器會將通知與讀取回條傳遞至 SMTP 上指定的位址**從**標頭。  
  
 **SMTP 伺服器驗證**  
  
 若您需要 SMTP 伺服器驗證，SMTP 傳送配接器會使用下列其中一個驗證類型：  
  
-   **基本。** SMTP 伺服器利用使用者提供的認證進行驗證。  
  
-   **處理序帳戶 (NTLM)。** SMTP 伺服器利用目前的程序認證進行驗證。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [設定 SMTP 配接器](../core/configuring-the-smtp-adapter.md)  
  
-   [設定 SMTP 配接器時的限制](../core/restrictions-when-configuring-the-smtp-adapter.md)  
  
-   [SMTP 配接器安全性建議](../core/smtp-adapter-security-recommendations.md)