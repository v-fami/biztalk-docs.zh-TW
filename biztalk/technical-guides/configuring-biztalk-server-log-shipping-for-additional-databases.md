---
title: "設定 BizTalk 記錄傳送的其他資料庫 |Microsoft 文件"
description: "加入自訂的資料庫備份 BizTalk Server 」 工作，以及 BizTalk Server 中的記錄傳送"
ms.custom: 
ms.date: 11/01/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fc2ae67-5cb9-4d53-9bf7-c88f84914960
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f4eb0b690f81b16d739183633c6507b2ad87226
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="configuring-biztalk-server-log-shipping-for-additional-databases"></a>設定 BizTalk Server 記錄傳送的其他資料庫

## <a name="overview"></a>概觀
在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，新增至 「 備份 BizTalk Server 」 工作的工作會自動加入至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送。 您不需要採取額外步驟來設定新的資料庫加入至 「 備份 BizTalk Server 」 工作的記錄傳送。 不過，請務必要將自訂資料庫加入視情況\<OtherDatabases > SampleUpdateInfo.xml 檔案的區段。 [設定記錄傳送的目的系統](../core/how-to-configure-the-destination-system-for-log-shipping.md)和[備份自訂資料庫](../core/how-to-back-up-custom-databases.md)提供一些指引。
  
## <a name="see-also"></a>另請參閱  
 [設定 BizTalk Server 記錄傳送](../technical-guides/configuring-biztalk-server-log-shipping.md)