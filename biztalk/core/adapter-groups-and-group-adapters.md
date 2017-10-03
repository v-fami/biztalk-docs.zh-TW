---
title: "配接器群組和群組配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e0a9423-99dd-4474-afa1-fd8e1d074cd1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fcf10f50857026893245cc567783b649f614c4f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-groups-and-group-adapters"></a>配接器群組和群組配接器
*配接器群組*是一種管理機制，您可以使用它來收集和組織的介面卡集合。 相反地，*群組配接器*是服務配接器群組中的所有配接器的元件。 例如，您可以撰寫一組配接器，讓它們都使用相同的 COM 元件，透過 TCP/IP 來傳輸密碼同步。 這一組配接器即稱為配接器群組，而用來服務這些配接器的元件，就稱為群組配接器。 配接器群組在組態存放區中加以描述。 您可以使用 `ISSOPSAdapter.ReceiveNotification` 擷取有關配接器群組的資訊和更新。  
  
 群組配接器的名稱和配接器群組的名稱相同。 除了命名限制不同之外，群組配接器其實就是一般的配接器。 例如，群組配接器可以擁有獨立存取群組和組態屬性，正如其組態檔案所述。 群組配接器大多和配接器群組中的配接器位於同一台電腦上。 然而，目前並不強制一定要如此做。 同樣地，相同配接器群組中的所有配接器最好都能在同一台電腦上。  
  
 您可以使用 `ISSOPSAdapter.InitializeAdapter`，在啟動時存取和初始化群組配接器。 當您初始化群組配接器時，系統會告知群組配接器，目前系統中有哪些配接器存在於配接器群組中。 此外，每當在配接器群組中新增、刪除、啟用或停用配接器時，系統將會傳送通知給群組配接器。 然而，群組配接器不會收到任何密碼變更通知。  
  
 配接器群組和群組配接器會選擇性使用管理工具。  
  
## <a name="see-also"></a>另請參閱  
 [密碼同步配接器](../core/password-sync-adapters.md)