---
title: POP3 配接器的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b6d621a2-4801-44fe-a266-d4c05ac82633
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bc86b2ae14b04b160f7387f870615116e659b3f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22261942"
---
# <a name="known-issues-with-the-pop3-adapter"></a>POP3 配接器的已知問題
本節包含可幫助您避免錯誤的資訊。  
  
## <a name="known-issues"></a>已知問題  
  
#### <a name="the-pop3-adapter-fails-to-process-documents-when-running-on-a-64-bit-operating-system"></a>POP3 配接器在 64 位元作業系統上執行時，無法處理文件  
  
##### <a name="problem"></a>問題  
 POP3 配接器在 64 位元作業系統上執行時，將無法處理文件。  
  
##### <a name="cause"></a>原因  
 POP3 配接器處理常式無法在 64 位元主控件執行個體上執行。  
  
##### <a name="resolution"></a>解決方案  
 如果您在 64 位元電腦上執行 POP3 配接器，則必須設定 POP3 配接器處理常式，使其在 32 位元主控件中執行。 此選項可在 [主控件屬性] 頁面上取得，您可從 BizTalk 管理主控台存取此頁面。  
  
## <a name="see-also"></a>另請參閱  
 [POP3 配接器疑難排解](../core/troubleshooting-the-pop3-adapter.md)