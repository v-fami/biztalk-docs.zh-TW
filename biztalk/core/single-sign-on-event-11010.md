---
title: "單一登入： 事件 11010 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22fcd9f3-83bb-44b0-88fc-197c2ef3e72d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f81bef87439c4607a32f2547d5bf44b19491140b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11010"></a>單一登入： 事件 11010
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|11010|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_WARN_NOT_SSO_AFF_ADMIN|  
|訊息文字|用戶端使用者不是 SSO 分支機構系統管理員 account.%r 的成員<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 用戶端使用者： %2\\%3 %r<br /><br /> SSO 分支機構系統管理員： %4|  
  
## <a name="explanation"></a>說明  
 用戶端使用者不是 SSO 分支機構系統管理員帳戶的成員。 稽核層級設定為高時，才會出現這個警告。  
  
## <a name="user-action"></a>使用者動作  
 若要補救這種情況，您必須進行用戶端使用者的 SSO 分支機構系統管理員帳戶的成員。 若要停止此警告訊息出現在未來，您可以降低稽核層級。