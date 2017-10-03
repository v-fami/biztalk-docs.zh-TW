---
title: "SMTP 配接器安全性建議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [SMTP adapters], security
- SMTP adapters, security
- security, SMTP adapters
ms.assetid: 45f13744-a0eb-4b4e-85cd-6b862b384ad5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca1aeed0ad8c80cc32d333aeef37d1da6feabfc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="smtp-adapter-security-recommendations"></a>SMTP 配接器安全性建議
您使用 SMTP 配接器透過 Simple Mail Transfer Protocol (SMTP) 通訊協定，交換執行 BizTalk Server 的伺服器與其他應用程式之間的資訊。 BizTalk Server 可建立電子郵件訊息並將它傳送到指定的電子郵件地址，將訊息傳送到其他應用程式。 您只可將 SMTP 配接器用於傳送訊息。 如需有關 SMTP 配接器的詳細資訊，請參閱[SMTP 配接器](../core/smtp-adapter.md)。  
  
 為執行 SMTP 配接器的主控件執行個體設定服務帳戶時，必須指定對遠端 SMTP 伺服器使用的驗證類型。 驗證選項有基本驗證 (純文字)、NTLM (使用目前認證) 或無 (若 SMTP 伺服器不需要驗證)。  
  
 使用 SMTP 配接器傳送訊息時，BizTalk Server 預設會以純文字傳送訊息。 若使用具有 S/MIME 編碼器元件的管線，在您將訊息傳送到 SMTP 伺服器之前可以先加密。 不過，SMTP 標頭仍會是純文字。  
  
 若要稽核 BizTalk Server 傳送的電子郵件訊息，應使用 SMTP 配接器連接到自己的 SMTP 伺服器，即可在此伺服器內稽核訊息。  
  
 SMTP 配接器不支援安全通訊端層 (SSL)。  
  
## <a name="see-also"></a>另請參閱  
 [接收和傳送伺服器的連接埠](../core/ports-for-the-receive-and-send-servers.md)   
 [最小安全性使用者權限](../core/minimum-security-user-rights.md)