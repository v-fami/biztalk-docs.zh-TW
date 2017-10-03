---
title: "SSO 伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, tasks
- Master Secret server, SSO
- servers, SSO
- SSO, servers
- SSO, Master Secret server
ms.assetid: 40240d6b-b7d1-48fb-b750-be0e380d52e3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37f2f24911a0336a734125436d97dbce6f9e0b77
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sso-server"></a>SSO 伺服器
「企業單一登入」(SSO) 伺服器可執行下列任何工作：  
  
-   **主要密碼伺服器當做函式。** 主要密碼伺服器會存放一份主要密碼或金鑰的保存複本，可用來加密 SSO 系統中的所有認證。 雖然主要密碼伺服器可做為查詢與管理的伺服器，但基於安全性理由，建議僅使用此伺服器做為主要密碼伺服器。 如需詳細資訊的函式主要密碼伺服器會執行，請參閱[主要密碼伺服器](../core/master-secret-server.md)。  
  
-   **執行管理作業。** SSO 系統管理員可以使用任何單一登入伺服器來執行管理工作，像是管理分支機構應用程式、設定使用者認證以及管理使用者對應。  
  
-   **執行查詢作業。** SSO 伺服器使用執行階段元件來查詢使用者認證。  
  
-   **發出與贖回票證。** SSO 伺服器還會發出與贖回 SSO 票證。  
  
-   **密碼同步處理。** 您可以在 SSO 伺服器上建立和管理密碼同步配接器。  
  
## <a name="see-also"></a>另請參閱  
 [使用 SSO](../core/using-sso.md)   
 [安裝 SSO](../core/installing-sso.md)