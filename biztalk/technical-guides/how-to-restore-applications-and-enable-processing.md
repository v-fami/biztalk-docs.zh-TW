---
title: 如何還原應用程式，並啟用處理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 83144965-a51a-481a-afd6-7f573b69badb
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65ae913d45f45b13458294863714823a41ff4e44
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22297830"
---
# <a name="how-to-restore-applications-and-enable-processing"></a>如何還原應用程式，並啟用處理
設定 BizTalk 群組中的應用程式，並啟用 > 主題所述的步驟之後的應用程式處理[如何更新執行階段電腦](../technical-guides/how-to-update-the-runtime-computers.md)。  
  
### <a name="to-enable-application-configuration-and-restore-application-processing"></a>若要啟用應用程式設定並還原應用程式處理  
  
1.  執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組中每個 BizTalk server 上的應用程式安裝 MSI 檔案。  
  
2.  執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定災害復原站台的應用程式群組中的一部伺服器上的應用程式組態 MSI 檔案。 接收位置和傳送埠會維持相同的名稱。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式組態 MSI 檔案會更新繫結，好讓這些成品指向嚴重損壞修復環境中正確的位置。  
  
    > [!NOTE]  
    >  如果接收位置和傳送埠不會影響生產網站遺失，它可能不需要重新設定應用程式與災害復原特定位置。  
  
3.  還原應用程式的程序藉由啟用所有的應用程式接收位置、 傳送埠，以及主控件執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [復原執行階段電腦](../technical-guides/recovering-the-runtime-computers.md)