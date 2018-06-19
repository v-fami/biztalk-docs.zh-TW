---
title: 準備進行災害復原的應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ef93099-aa6b-424a-a4ce-87d855c6afe3
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7028b1386f71f653dfc41b9de2522cdbd8d02126
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302334"
---
# <a name="preparing-applications-for-disaster-recovery"></a>準備進行災害復原的應用程式
BizTalk 應用程式 （二進位檔和設定成品例如接收位置和傳送埠） 會部署到生產環境 BizTalk 群組中，當群組在災害復原站台上還原。 此設定可能要改變取決於是否有設定位置例如接收位置和傳送實際執行環境專屬的連接埠。  
  
 為加速還原的應用程式在災害復原站台， [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] .msi 檔案安裝二進位檔上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段伺服器必須保持最新的災害復原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段伺服器。 在災害復原站台還原的實際執行的 BizTalk 群組時，可能需要災害復原特定應用程式組態.msi 檔案安裝，才能設定應用程式災害復原特定成品，例如接收位置和傳送埠，視。  
  
## <a name="see-also"></a>另請參閱  
 [部署應用程式](../technical-guides/deploying-an-application.md)