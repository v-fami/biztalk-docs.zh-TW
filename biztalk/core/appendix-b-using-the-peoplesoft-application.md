---
title: 附錄 b： 使用 PeopleSoft 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PeopleSoft, using
- using PeopleSoft application
ms.assetid: 36475836-1d23-4bb4-a3c1-cdd3fff28476
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bbe0bba08421360364fb668be9ae4d980d7a54d8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25964140"
---
# <a name="appendix-b-using-the-peoplesoft-application"></a>附錄 b： 使用 PeopleSoft 應用程式
本節說明如何使用有助您完成協調流程測試的不同 PeopleSoft 區域。  
  
 當您針對接收埠使用 PeopleSoft 時，可以使用 PeopleTools 來建立 XML 文件。 不需要特別動作就能與 PeopleSoft 互動。 事件，您必須能夠存取**http\\\\:\<主機\>:\<連接埠\>** 來接聽來自 PeopleSoft 的事件。 如果您無法使用主機和連接埠，您可以設定 PeopleSoft Integration Broker 來設定 HTTP 主機和連接埠。  
  
 若要完成測試 PeopleSoft 接收埠，[產生的 XML 或結構描述在 PeopleSoft 中的](../core/generating-xml-or-schema-in-peoplesoft.md)討論如何藉由變更 PeopleSoft 環境中的事物觸發 PeopleSoft 事件。 這項變更會啟用 XML 檔案，該檔案會傳送至您在協調流程中設定要監控的資料夾中。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [在 PeopleSoft 中產生 XML 或結構描述](../core/generating-xml-or-schema-in-peoplesoft.md)  
  
-   [建立 PeopleSoft HTTP 主控件和連接埠](../core/creating-a-peoplesoft-http-host-and-port.md)