---
title: 接收配接器作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b61ea356-f2a1-4604-8e52-13d2961399d0
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d4e5ee9d9afbbb687f415b42652d76a50bac4bf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980119"
---
# <a name="receive-adapter-operations"></a>接收配接器作業
接收配接器可以執行下列作業：  

- **單向提交： void SubmitMessage (IBaseMessage msg)。** 從接收埠收到訊息之後，此配接器會將它提交給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，供訂閱的協調流程或傳送埠處理。  

- **暫止： void MoveToSuspendQ (IBaseMessage msg)。** 當配接器判斷在提交之後發生了剖析、傳輸、序列化或其他適用的失敗時，它會將訊息移到擱置的佇列。  

- **提交要求： void SubmitRequestMessage （IBaseMessage requestMsg，字串 correlationToken，[marshalas （unmanagedtype.bool)] bool firstResponseOnly，DateTime expirationTime，IBTTransmitter responseCallback）。** 接收配接器會將內送訊息以要求-回應組的方式提交給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 成功處理這個要求訊息之後，它會將回應傳送給此配接器，以將它傳輸給特定的端點。
