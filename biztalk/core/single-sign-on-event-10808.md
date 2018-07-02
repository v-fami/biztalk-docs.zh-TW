---
title: 單一登入： 事件 10808 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b4efc1d-f163-4440-a78e-53065c6af36c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49d4e6ab0f6a9ea10ef28440f5b8399778fbc93b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971399"
---
# <a name="single-sign-on-event-10808"></a>單一登入： 事件 10808
## <a name="details"></a>詳細資料  
  
|                 |                                                                  |
|-----------------|------------------------------------------------------------------|
|  產品名稱   |                    企業單一登入                     |
| 產品版本 |    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]    |
|    事件識別碼     |                              10808                               |
|  事件來源   |                              ENTSSO                              |
|    元件    |                               不適用                                |
|  符號名稱  |                ENTSSO_E_HISSO_SYSTEM_NOT_ENABLED                 |
|  訊息文字   | SSO 系統不會啟用主控件初始化的單一登入。 |
  
## <a name="explanation"></a>說明  
 SSO 系統不會啟用主控件初始化的單一登入。  
  
## <a name="user-action"></a>使用者動作  
 使用系統管理工具來設定主應用程式起始單一登入。 這將會設定  
  
 全域資訊 SSO_FLAG_SSO_EXTERNAL_TO_WINDOWS 旗標。