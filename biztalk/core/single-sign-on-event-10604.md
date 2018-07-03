---
title: 單一登入： 事件 10604 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eea14ab1-5a89-4a62-b414-1bcb36ea339e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48996ec333c9035e57393e270db06ca173cfc9e6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990583"
---
# <a name="single-sign-on-event-10604"></a>單一登入： 事件 10604
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                          |
|-----------------|----------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                        企業單一登入                                         |
| 產品版本 |                        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                        |
|    事件識別碼     |                                                  10604                                                   |
|  事件來源   |                                                  ENTSSO                                                  |
|    元件    |                                                   不適用                                                    |
|  符號名稱  |                                      SSO_ERROR_SSOCSTX_OUT_OF_PROC                                       |
|  訊息文字   | ' ENTSSO Server' COM + 應用程式未正確設定。 它必須是 COM + 程式庫應用程式。 |
  
## <a name="explanation"></a>說明  
 COM + 應用程式必須設定為 COM + 程式庫應用程式。  
  
## <a name="user-action"></a>使用者動作  
 在 ENTSSO MMC 嵌入式管理單元中，展開 COM + 資料夾，並找出對 ENTSSO 伺服器。 以滑鼠右鍵按一下伺服器，然後按一下 屬性。 選取程式庫應用程式，而不是伺服器應用程式，然後按一下 [確定]。