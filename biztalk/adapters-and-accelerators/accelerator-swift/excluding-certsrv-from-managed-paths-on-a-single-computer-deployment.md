---
title: 排除 CertSrv 從受管理的路徑上的單一電腦部署 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed paths
- certificate server (CertSrv)
- certificates, certificate server (CertSrv)
ms.assetid: 39916663-b80e-49d8-ba9b-49276eb564fc
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c77fc1733859cd903bafcebc26162323feff82d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207430"
---
# <a name="excluding-certsrv-from-managed-paths-on-a-single-computer-deployment"></a>從單一電腦部署受管理的路徑排除 CertSrv
如果您已部署[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]在單一電腦上，而且也安裝憑證伺服器的相同電腦上，您需要從受管理的路徑中排除憑證伺服器 (CertSrv) [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] SharePoint Server 管理中心。  
  
### <a name="to-exclude-certsrv-from-the-managed-paths"></a>若要從受管理的路徑排除 CertSrv  
  
1.  按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下**SharePoint 管理中心內**。  
  
2.  在 [管理中心] 視窗中**虛擬伺服器設定**區段中，按一下**設定虛擬伺服器設定**。  
  
3.  在 [虛擬伺服器清單] 視窗中，按一下**Default Web Site**。  
  
4.  在 [虛擬伺服器設定] 視窗中**虛擬伺服器管理**區段中，按一下**定義管理的路徑**。  
  
5.  在 [定義管理的路徑] 視窗中**新增路徑**區段中，輸入**CertSrv**中**路徑**文字方塊。 在**類型**區段中，按一下**排除的路徑**。 按一下 **[確定]**。  
  
6.  關閉 [定義管理的路徑] 視窗。