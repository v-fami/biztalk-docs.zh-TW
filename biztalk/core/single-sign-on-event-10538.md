---
title: 單一登入： 事件 10538 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1211ac33-9149-4dd3-85a2-d46eb24d1060
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f4b7fba63d26fde664e14470eb95b41a1580ae7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975775"
---
# <a name="single-sign-on-event-10538"></a>單一登入： 事件 10538
## <a name="details"></a>詳細資料  

|                 |                                                                           |
|-----------------|---------------------------------------------------------------------------|
|  產品名稱   |                         企業單一登入                         |
| 產品版本 |        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]         |
|    事件識別碼     |                                   10538                                   |
|  事件來源   |                                  ENTSSO                                   |
|    元件    |                                    CO                                     |
|  符號名稱  |                           SSO_WARN_APP_DISABLED                           |
|  訊息文字   | 正在 disabled.%r 應用程式。<br /><br /> 應用程式名稱： %1 |

## <a name="explanation"></a>說明  
 這個警告事件表示，SSO 分支機構應用程式已停用的應用程式系統管理員。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列一或多個動作：  

- 請連絡您的應用程式系統管理員，以啟用 SSO 分支機構應用程式。 這可以使用 SSO 管理工具 （GUI 或命令列）。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [如何啟用分支機構應用程式](../core/how-to-enable-an-affiliate-application.md)  

- [如何停用分支機構應用程式](../core/how-to-disable-an-affiliate-application.md)
