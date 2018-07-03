---
title: 單一登入： 事件 10611 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4549ac01-b828-478f-aea0-862e14fac149
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ca43eff86b20df7000c973f7c6ade472a8780de
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023564"
---
# <a name="single-sign-on-event-10611"></a>單一登入： 事件 10611
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                           |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                         企業單一登入                                                                                                         |
| 產品版本 |                                                                                        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                         |
|    事件識別碼     |                                                                                                                   10611                                                                                                                   |
|  事件來源   |                                                                                                                  ENTSSO                                                                                                                   |
|    元件    |                                                                                                                    不適用                                                                                                                    |
|  符號名稱  |                                                                                                     SSO_INFO_SERVICE_STARTING_NO_SSL                                                                                                      |
|  訊息文字   | SSO 服務正在 starting.%r<br /><br /> 電腦名稱: %1 %r<br /><br /> SQL Server 名稱: %2 %r<br /><br /> SSO 資料庫名稱: %3 %r<br /><br /> 未使用 SSL。 如何保護 SQL Server 連接，請參閱文件，如需詳細資訊。 |
  
## <a name="explanation"></a>說明  
 ENTSSO 服務正在啟動而不使用安全通訊端層 (SSL)。 建議您從 SSO 服務保護您的連線，to SQL。  
  
## <a name="user-action"></a>使用者動作  
 請參閱文件，網址[如何啟用 SSO 的 SSL](../core/how-to-enable-ssl-for-sso.md)  
  
 執行個體時提供 SQL Server 登入。