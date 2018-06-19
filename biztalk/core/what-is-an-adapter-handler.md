---
title: 什麼是配接器處理常式？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- handlers [adapters]
- adapters, handlers
- handlers [adapters], about handlers
ms.assetid: 4d1afa39-6320-467f-a7e8-f5f18236648e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c8a1b60661427776dd4e35ffce27bf120bf94a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289302"
---
# <a name="what-is-an-adapter-handler"></a>什麼是配接器處理常式？
配接器處理常式是 BizTalk 主控件的執行個體，配接器程式碼會在其中執行。 當您指定配接器的傳送或接收處理常式時，就是指定配接器程式碼將在哪個主控件執行個體的內容中執行。 配接器處理常式負責執行配接器，並且含有配接器的特定執行個體之屬性。 預設的 BizTalk Server 組態將為所有已安裝的配接器建立配接器處理常式，但您可能想為負載平衡考量而建立其他配接器處理常式，或為特定配接器處理常式提供程序隔離。  
  
 配接器處理常式與 BizTalk 主控件執行個體繫結，而 BizTalk 主控件執行個體與 BizTalk 伺服器繫結。 因此，若想要負載平衡所有 BizTalk 伺服器的配接器處理，必須新增其他 BizTalk 伺服器到 BizTalk 群組中。 若針對程序隔離考量而建立其他配接器處理常式，就不需新增其他 BizTalk 伺服器到 BizTalk 群組中。  
  
 若需要建立執行配接器處理常式的新主控件執行個體，必須先建立主控件，然後建立該主控件的執行個體以在其中一個 BizTalk 伺服器上執行。 如需詳細資訊，請參閱[如何建立新的主控件](../core/how-to-create-a-new-host.md)和[如何新增主控件執行個體](../core/how-to-add-a-host-instance.md)。  
  
 除了 HTTP 與 SOAP 配接器接收處理常式以外的所有配接器處理常式，都必須設定成在內含式主控件中執行。 HTTP 和 SOAP 配接器接收處理常式只能在外掛式主控件中執行。  
  
## <a name="see-also"></a>另請參閱  
 [建立和刪除配接器處理常式](../core/creating-and-deleting-adapter-handlers.md)