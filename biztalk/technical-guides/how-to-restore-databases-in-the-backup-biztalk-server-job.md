---
title: 如何還原 「 備份 BizTalk Server 」 工作中的資料庫 |Microsoft 文件
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
ms.openlocfilehash: eb7c52b810343c1807e982e637372c74baeb84fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298558"
---
# <a name="how-to-restore-databases-in-the-backup-biztalk-server-job"></a>如何還原 「 備份 BizTalk Server 」 工作中的資料庫
本章節涵蓋上線所備份的 「 備份 BizTalk Server 」 工作的 BizTalk 群組中資料庫的步驟。 根據預設，所有資料庫都備份可以使用備份 BizTalk Server 作業，除了 BAM 資料庫。 請參閱[還原 Analysis Services 和支援的資料庫](../technical-guides/restoring-analysis-services-and-supporting-databases.md)如需備份和還原 BAM 資料庫的詳細資訊。 您必須將所有資料庫還原為相同的標記，以確保資料庫間的交易狀態一致。 如需詳細資訊，請參閱[標示的交易、 完整備份和記錄檔備份](http://go.microsoft.com/fwlink/?LinkId=151565)(http://go.microsoft.com/fwlink/?LinkId=151565)。  
  
 如需詳細資訊和指示，關於還原資料庫的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[如何還原您的資料庫](http://go.microsoft.com/fwlink/?LinkId=151406)(http://go.microsoft.com/fwlink/?LinkId=151406)。  
  
## <a name="see-also"></a>另請參閱  
 [還原資料庫不包含在備份 BizTalk Server 作業](../technical-guides/restoring-databases-not-included-in-the-backup-biztalk-server-job.md)