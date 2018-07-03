---
title: 單一登入： 事件 10594 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f4c6041-39a8-49bc-b39e-66cb6eb2efae
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba733d9a919b2af09824242a48a2fa85af8ab481
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004758"
---
# <a name="single-sign-on-event-10594"></a>單一登入： 事件 10594
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                 企業單一登入                                                                                  |
| 產品版本 |                                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                 |
|    事件識別碼     |                                                                                           10594                                                                                            |
|  事件來源   |                                                                                           ENTSSO                                                                                           |
|    元件    |                                                                                            不適用                                                                                             |
|  符號名稱  |                                                                              SSO_WARN_TICKET_VALIDATE_FAILED                                                                               |
|  訊息文字   | 驗證票證失敗。 寄件者名稱必須符合票證 issuer.%r<br /><br /> 應用程式名稱: %1 %r<br /><br /> 票證發出者: %2 %r<br /><br /> 寄件者名稱： %3 |
  
## <a name="explanation"></a>說明  
 為了讓驗證票證，必須符合票證核發者和寄件者名稱中的欄位 （警告訊息）。 不過，透過 BizTalk 不受信任主應用程式傳送訊息，寄件者名稱會變更名稱之 BizTalk 不受信任的主控件，則將不會驗證票證。  
  
## <a name="user-action"></a>使用者動作  
 如果您使用企業單一登入，請確定您的訊息會流經只能透過受信任的 BizTalk 主控件。 這會減少訊息中的資料遭竄改的風險。  
  
 如果您完全了解的安全性影響您的案例，您可以關閉此應用程式的驗證。 請注意，驗證可以在系統或只是此特定應用程式關閉的管理選項。