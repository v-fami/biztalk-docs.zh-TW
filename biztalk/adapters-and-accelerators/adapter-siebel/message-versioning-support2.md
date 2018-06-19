---
title: 訊息版本控制 Support2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message versioning, support for
ms.assetid: 5b7b9202-9f45-450e-918f-b26a03711aab
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04514a9c55fa29a930b6ba7467177d6a754ff3db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22221854"
---
# <a name="message-versioning-support"></a>訊息版本控制支援
[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]訊息動作、 命名空間和節點識別碼中包含的版本字串元件的支援版本控制作業中顯示。 目前的版本是 http://Microsoft.LobServices.Siebel/2007/03。 這表示在 Siebel 儲存機制中的帳戶商務物件上插入作業，配接器所顯示的插入作業具有下列：  
  
-   節點 ID: http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
  
-   訊息的動作： http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
  
-   命名空間： http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Operation  
  
> [!NOTE]
>  這項功能不提供與舊版配接器的回溯相容性。  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)