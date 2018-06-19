---
title: 使用 BizTalk Server 和 WCF LOB 配接器 SDK |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 43ff0357-76e6-42bc-a1f7-0385d9378a5f
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41fffdf81d6e5565f9799594ddee485be485fed4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22226014"
---
# <a name="using-biztalk-server-and-the-wcf-lob-adapter-sdk"></a>使用 BizTalk Server 和 WCF LOB 配接器 SDK
此章節包含的關聯性的相關資訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 本節包含的資訊包括每個所提供的兩個不同架構的比較及移轉的提示[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]自訂配接器。  
  
## <a name="relationship-with-the-sdk-and-biztalk-server"></a>BizTalk Server SDK 與關聯性
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供的 SDK 和一組工具和元件，讓開發人員撰寫複雜的配接器的特定業務系統包含動態集的作業和資料。 配接器會公開為 WCF 自訂繫結，因此可使用的 WCF 繫結應用程式可以取用。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]是一項產品，可讓訊息流程和協調多樣的企業系統。之間的通訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和外部系統都是透過將外部的訊息，並將它們轉換成適用於處理格式的配接器處理[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
 這兩個技術交集在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]WCF 配接器。 它可以取用 WCF 所公開的繫結和作業和寫入與配接器所公開的資料，因此使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。  
  
 下圖提供如何使用 BizTalk WCF 配接器和 WCF LOB 配接器內的高階概觀[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]與目標 LOB 系統進行通訊。  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/8dd622c6-ab5e-4cd9-aa86-5176f5c62203.gif "8dd622c6-ab5e-4cd9-aa86-5176f5c62203")  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/4f503084-da4f-41cb-92b9-eaea25d1b456.gif "4f503084-da4f-41cb-92b9-eaea25d1b456")  

## <a name="differences-between-the-sdk-and-the-biztalk-server-adapter-framework"></a>SDK 和 BizTalk Server 配接器架構之間的差異

雖然兩個[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]配接器架構提供 SDK 撰寫自訂配接器、 那里顯著的差異，支援的數量 API 以提供與工具，而且也中重複使用性的配接器一次已完成。  
  
 下表摘要說明一些這兩個架構之間的主要差異。  
  
|功能|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]|[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]配接器架構|  
|---|---|---|  
|API|[!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]和[!INCLUDE[dotnet451](../../includes/dotnet451-md.md)]組件，提供說明類別用於處理連接管理和傳訊的中繼資料|COM，配接器作業提供基本支援。|  
|配接器的風險|公開為 WCF 繫結。可用於任何應用程式可以取用 WCF 繫結。|僅公開[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]; 其他應用程式不可重複使用。|  
|工具|[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]中繼資料的瀏覽器[!INCLUDE[btsVStudioNet](../../includes/btsvstudionet-md.md)]|n/a|  
|擴充性|Yes （如 WCF 通道延伸模組）|否|  
  
 使用 BizTalk 配接器架構所建立的配接器是您可以從使用只在 BizTalk Server 內。 另一方面，配接器寫入[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]當成自訂 WCF 繫結。 這會放寬觸角任何應用程式取用服務，這實際上是任何.NET 應用程式，包括[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 WCF 配接器內使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]使用 BizTalk WCF 配接器，並繼續存在於原生 BizTalk 配接器與並行。 
 
