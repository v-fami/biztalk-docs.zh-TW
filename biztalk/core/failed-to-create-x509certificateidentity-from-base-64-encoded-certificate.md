---
title: 無法從 base-64 編碼憑證建立 X509CertificateIdentity |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13112bd-e0e8-4b49-ad2f-ea82b2e8162f
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00d92c9ca3f7de567de915241d5950f5b93c06da
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995239"
---
# <a name="failed-to-create-x509certificateidentity-from-base-64-encoded-certificate"></a>無法從 Base-64 編碼憑證建立 X509CertificateIdentity。
## <a name="details"></a>詳細資料  

|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  產品名稱   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| 產品版本 |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    事件識別碼     |                                         0                                          |
|  事件來源   |                                         0                                          |
|    元件    |                                         0                                          |
|  符號名稱  |                                         0                                          |
|  訊息文字   |     無法從 Base-64 編碼憑證建立 X509CertificateIdentity。      |

## <a name="explanation"></a>說明  
 此錯誤表示配接器因為無效的憑證設定，而無法建立 X509Certificate 結束點識別。  

## <a name="user-action"></a>使用者動作  
 使用下列程序來設定憑證。  

#### <a name="to-configure-certificates"></a>若要設定憑證  

1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。  

2. 在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  

3. 找出您的應用程式，然後找出您的傳輸。  

4. 以滑鼠右鍵按一下傳輸名稱。  

5. 按一下 **[屬性]**。  

6. 在 連接埠**型別**清單中，選取正確的連接埠。  

7. 按一下 **設定**。  

8. 在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**安全性**] 索引標籤。  

9. 確保設定正確**用戶端憑證指紋**並**的服務憑證指紋**。
