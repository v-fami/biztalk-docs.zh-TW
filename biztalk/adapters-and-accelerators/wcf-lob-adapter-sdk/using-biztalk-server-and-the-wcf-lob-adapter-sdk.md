---
title: 使用 BizTalk Server 和 WCF LOB 配接器 SDK |Microsoft Docs
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
ms.openlocfilehash: 46b06f832fd9ff36f0e274c1599b577bc9ec6010
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989975"
---
# <a name="using-biztalk-server-and-the-wcf-lob-adapter-sdk"></a>使用 BizTalk Server 和 WCF LOB 配接器 SDK
此章節包含的關聯性的相關資訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 本節包含的資訊包含的每個所提供的兩個不同架構的比較，以及移轉秘訣[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]自訂配接器。  

## <a name="relationship-with-the-sdk-and-biztalk-server"></a>SDK 與 BizTalk Server 的關聯性
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] 提供的 SDK 和一組工具和元件可讓開發人員撰寫複雜的配接器，其中包含一組動態的作業和資料的特定業務系統。 配接器會公開為 WCF 自訂繫結，因此可以由應用程式，可以使用 WCF 繫結。  

 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 是一項產品，可讓訊息流程和協調一組多樣化的企業系統;之間的通訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]與外部系統透過採用外部的訊息，並將它們轉換成適用於處理格式的配接器處理[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  

 這兩種技術交集在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]WCF 配接器。 它可以取用 WCF 所公開的繫結，因此耗用 operations 主控台和公開的配接器與寫入資料[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。  

 下圖提供如何使用 BizTalk WCF 配接器和 WCF LOB 配接器內的高階概觀[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]目標 LOB 系統與通訊。  

 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/8dd622c6-ab5e-4cd9-aa86-5176f5c62203.gif "8dd622c6-ab5e-4cd9-aa86-5176f5c62203")  

 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/4f503084-da4f-41cb-92b9-eaea25d1b456.gif "4f503084-da4f-41cb-92b9-eaea25d1b456")  

## <a name="differences-between-the-sdk-and-the-biztalk-server-adapter-framework"></a>SDK 和 BizTalk Server 配接器架構之間的差異

雖然兩個[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]配接器架構提供的 SDK 來撰寫自訂配接器那里是支援數量相當大的差異提供以 API 和工具，也在一次的配接器的重複使用是已完成。  

 下表中摘要說明一些這兩個架構的主要差異。  


|     功能      |                                                                   [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]                                                                   |                  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 配接器架構                   |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
|       API        | [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)] 和[!INCLUDE[dotnet451](../../includes/dotnet451-md.md)]組件，提供中繼資料處理、 連線管理和傳訊的說明類別 |                                            COM，配接器作業提供基本的支援。                                             |
| 配接器的曝光度 |                                                            公開為 WCF 繫結;供任何應用程式可以取用 WCF 繫結。                                                             | 只公開[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]; 不可重複使用其他應用程式。 |
|      工具       |                       [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]為中繼資料瀏覽器 [!INCLUDE[btsVStudioNet](../../includes/btsvstudionet-md.md)]                       |                                                                    n/a                                                                     |
|  擴充性   |                                                                                       [是] （作為 WCF 通道擴充功能）                                                                                        |                                                                     否                                                                     |

 使用 BizTalk 配接器架構所建立的配接器是從 BizTalk Server 內只可取用的。 另一方面，配接器寫入[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]當成自訂 WCF 繫結。 這會放寬觸角任何應用程式，使用服務，這實際上是任何.NET 應用程式，包括[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 WCF 架構配接器內使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]使用 BizTalk WCF 配接器，並繼續使用原生的 BizTalk 配接器同時存在。 

