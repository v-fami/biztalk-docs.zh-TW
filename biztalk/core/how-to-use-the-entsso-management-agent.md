---
title: 如何使用 ENTSSO 管理代理程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c89b494-db12-4d2a-a030-6acd34489cab
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68c354f2250e9abc6a02ea52f4b7c106f57144e6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018474"
---
# <a name="how-to-use-the-entsso-management-agent"></a>如何使用 ENTSSO 管理代理程式
此版本的企業單一登入 (SSO) 包含 Microsoft Identity Integration Server (MIIS) 的管理代理程式 (MA)，整合了企業單一登入與 MIIS 的帳戶同步處理功能。 這樣一來 MIIS 系統管理員即可管理 SSO 資料庫內的 SSO 對應。  
  
 在 企業單一登入，Windows 網域帳戶之間建立對應 (*domainname\username*) 和外部認證。 如果您有 Active Directory 管理代理程式，並管理代理程式的外部資料來源 (範例： RACF MA)，您可以使用企業單一登入 (ENTSSO MA) 管理 SSO 資料庫中的對應。 ENTSSO MA 是*呼叫為基礎的匯出*只管理代理程式。  
  
 設定管理代理程式可分三部分：  
  
- 組態檔 (ENTSSO.xml)  
  
- MIIS 使用者介面  
  
- ENTSSO 使用者介面  
  
  此章節的主題會說明該組態程序。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [設定 XML 檔案](../core/configuring-the-xml-file.md)  
  
-   [如何設定 ENTSSO MA 的 MIIS](../core/how-to-configure-miis-for-entsso-ma.md)  
  
-   [如何設定 ENTSSO 以進行 MIIS 密碼同步](../core/how-to-configure-entsso-for-miis-password-sync.md)