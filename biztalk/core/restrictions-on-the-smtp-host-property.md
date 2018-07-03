---
title: SMTP 主控件屬性的限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [SMTP adapters], restrictions
- SMTP adapters, restrictions
ms.assetid: 6dbdb6dc-0062-4444-a4c8-6e2a7900f533
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2e8ef3800b67119bf9ffaffb4fd069064b640d1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985343"
---
# <a name="restrictions-on-the-smtp-host-property"></a>SMTP 主控件屬性限制
SMTP 主控件屬性是一個字串，可指定 SMTP 配接器從 BizTalk 伺服器傳送訊息時將使用的 SMTP 伺服器。  
  
 下列規則和限制適用於此屬性：  
  
- 此屬性必須設定在配接器處理常式層級、端點層級或同時設定。  
  
- SMTP 伺服器屬性不能包含下列字元: ' ~ ！ @ # $ ^ & * ( ) = + [ ] { } \ &#124; ; : ' " , \< \> /, ?;  
  
- SMTP 伺服器名稱的長度不可以超過 256 個字元。  
  
  SMTP 配接器永遠會使用先前提及的規則，在設計階段驗證 SMTP 主控件名稱。 此外，若訊息是透過動態連接埠以 SMTP 配接器來傳送，則 SMTP 配接器會在執行階段驗證 SMTP 主控件名稱。  
  
## <a name="see-also"></a>另請參閱  
 [設定 SMTP 配接器的限制](../core/restrictions-when-configuring-the-smtp-adapter.md)