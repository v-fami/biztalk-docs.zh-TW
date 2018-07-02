---
title: 如何還原資料庫，在 「 備份 BizTalk Server 」 工作中的 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9bcac40f-ef0b-4ff0-8743-cf1614e14422
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fde33b46937118aa29aa8259225da2c4d2c0439
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992407"
---
# <a name="how-to-restore-databases-in-the-backup-biztalk-server-job"></a>如何還原資料庫中備份 BizTalk Server 作業
本章節涵蓋上線的資料庫會由 「 備份 BizTalk Server 」 工作在 BizTalk 群組中的步驟。 根據預設，所有資料庫會都由使用 「 備份 BizTalk Server 」 作業，除了 BAM 資料庫。 請參閱[還原 Analysis Services 和支援資料庫](../technical-guides/restoring-analysis-services-and-supporting-databases.md)如需備份和還原 BAM 資料庫的詳細資訊。 您必須將所有資料庫還原為相同的標記，以確保資料庫間的交易狀態一致。 如需詳細資訊，請參閱 <<c0> [ 標示的交易、 完整備份和記錄備份](http://go.microsoft.com/fwlink/?LinkId=151565)(http://go.microsoft.com/fwlink/?LinkId=151565)。  
  
 如需詳細資訊和指示還原資料庫的相關[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 還原您的資料庫如何](http://go.microsoft.com/fwlink/?LinkId=151406)(<http://go.microsoft.com/fwlink/?LinkId=151406>)。  
  
## <a name="see-also"></a>另請參閱  
 [還原不包含在備份 BizTalk Server 作業中的資料庫](../technical-guides/restoring-databases-not-included-in-the-backup-biztalk-server-job.md)