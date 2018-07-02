---
title: 單一登入： 事件 10532 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae2112bc-b53c-4d99-9dc1-a2f55dda4665
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 135060013686ff24e4f2692bda0e8829189e1c4a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974847"
---
# <a name="single-sign-on-event-10532"></a>單一登入： 事件 10532
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                     |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                              企業單一登入                                                                              |
| 產品版本 |                                                             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                              |
|    事件識別碼     |                                                                                        10532                                                                                        |
|  事件來源   |                                                                                       ENTSSO                                                                                        |
|    元件    |                                                                                         CO                                                                                          |
|  符號名稱  |                                                                             SSO_WARN_LOST_SECRET_SERVER                                                                             |
|  訊息文字   | 無法擷取主要密碼。 確認主要密碼伺服器名稱是否正確以及是否可用。%r<br /><br /> 祕密伺服器名稱: %1 %r<br /><br /> 錯誤碼： %2 |

## <a name="explanation"></a>說明  
 這個警告事件表示取得主要密碼的要求已經失敗。 這可能是因為「企業單一登入」服務未在伺服器上執行。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列一或多個動作：  

- 檢查應用程式事件記錄檔相關聯的事件或錯誤。  

- 請確認主要密碼伺服器名稱是正確的。  

- 請確認主要密碼伺服器連線且「企業單一登入」服務正在執行。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [如何產生主要密碼](../core/how-to-generate-the-master-secret.md)  

- [管理主要密碼](../core/managing-the-master-secret.md)
