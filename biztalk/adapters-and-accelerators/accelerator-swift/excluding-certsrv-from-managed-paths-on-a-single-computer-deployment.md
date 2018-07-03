---
title: 排除 CertSrv 從受管理的路徑上的單一電腦部署 |Microsoft Docs
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
ms.openlocfilehash: 1651131369ef4a8e0c4683b82f5b97163e33382f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987839"
---
# <a name="excluding-certsrv-from-managed-paths-on-a-single-computer-deployment"></a>從單一電腦部署的受管理路徑中排除 CertSrv
如果您已部署[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]在單一電腦上也安裝了憑證伺服器的相同電腦上，您需要排除憑證伺服器 (/certsrv) 從 Microsoft SharePoint Server 管理中心 中受管理的路徑。  
  
### <a name="to-exclude-certsrv-from-the-managed-paths"></a>若要從受管理的路徑中排除 CertSrv  
  
1.  按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下**SharePoint 管理中心**。  
  
2.  在 [管理中心] 視窗中，在**虛擬伺服器組態**區段中，按一下**設定虛擬伺服器設定**。  
  
3.  在 [虛擬伺服器清單] 視窗中，按一下**Default Web Site**。  
  
4.  在 [虛擬伺服器設定] 視窗中，在**虛擬伺服器管理**區段中，按一下**定義管理的路徑**。  
  
5.  在 [定義管理的路徑] 視窗中，在**加入新路徑**區段中，輸入**CertSrv**中**路徑**文字方塊。 在 **型別**區段中，按一下**排除的路徑**。 按一下 [確定] 。  
  
6.  關閉 [定義管理的路徑] 視窗。