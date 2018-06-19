---
title: 建立 MSMQ 接收位置和傳送埠從程式碼 |Microsoft 文件
description: 以程式設計方式建立 MSMQ 接收位置和 BizTalk Server 中的傳送埠
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6ebb4119-deeb-4287-aa65-7597ff0cc435
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5f00a0bfe14eeb7d4205973b3fef96e23026616
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971668"
---
# <a name="create-msmq-receive-locations-and-send-ports-programmatically"></a><span data-ttu-id="fb369-103">以程式設計方式建立 MSMQ 接收位置和傳送埠</span><span class="sxs-lookup"><span data-stu-id="fb369-103">Create MSMQ Receive Locations and Send Ports programmatically</span></span>
<span data-ttu-id="fb369-104">本主題將說明如何使用 WMI 來建立 MSMQ 配接器的連接埠或位置。</span><span class="sxs-lookup"><span data-stu-id="fb369-104">This topic explains how to use WMI to create a port or location for the MSMQ adapter.</span></span>  
  
 <span data-ttu-id="fb369-105">如需詳細資訊，請參閱**與日期時間排程組態使用 WMI 建立接收位置** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="fb369-105">For more information, see **Creating a Receive Location with a Datetime Schedule Configuration Using WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="setting-property-values"></a><span data-ttu-id="fb369-106">設定屬性值</span><span class="sxs-lookup"><span data-stu-id="fb369-106">Setting Property Values</span></span>  
 <span data-ttu-id="fb369-107">建立連接埠或位置的程序都是相同的：</span><span class="sxs-lookup"><span data-stu-id="fb369-107">The process of creating a port or location is always the same:</span></span>  
  
1.  <span data-ttu-id="fb369-108">建立正確型別的物件。</span><span class="sxs-lookup"><span data-stu-id="fb369-108">Create an object of the right type.</span></span>  
  
2.  <span data-ttu-id="fb369-109">設定物件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="fb369-109">Set the value of properties on the object.</span></span>  
  
3.  <span data-ttu-id="fb369-110">認可物件值到資料庫。</span><span class="sxs-lookup"><span data-stu-id="fb369-110">Commit the object values to the database.</span></span>  
  
 <span data-ttu-id="fb369-111">所有介面卡都有特定的屬性，例如**HostName**通用。</span><span class="sxs-lookup"><span data-stu-id="fb369-111">All adapters have certain properties, such as **HostName**, in common.</span></span> <span data-ttu-id="fb369-112">您可以用直接指派到物件的方式來設定這些通用屬性。</span><span class="sxs-lookup"><span data-stu-id="fb369-112">You set these common properties by directly assigning them to the object.</span></span> <span data-ttu-id="fb369-113">以下 C# 程式碼所示就是這種典型範例：</span><span class="sxs-lookup"><span data-stu-id="fb369-113">The following C# code shows a typical case:</span></span>  
  
```  
objReceiveLocation["HostName"] = "BizTalkServerApplication";  
```  
  
 <span data-ttu-id="fb369-114">您為非所有配接器所共用的屬性指派值。</span><span class="sxs-lookup"><span data-stu-id="fb369-114">You assign values to properties that not all adapters share.</span></span> <span data-ttu-id="fb369-115">您用字串建立 XML 文件，並將該字串指派給 CustomCfg 屬性。</span><span class="sxs-lookup"><span data-stu-id="fb369-115">You create an XML document in a string and assign that string to the CustomCfg property.</span></span> <span data-ttu-id="fb369-116">以下 C# 程式碼所示就是典型的 FILE 配接器範例：</span><span class="sxs-lookup"><span data-stu-id="fb369-116">The following C# code shows a typical case for a FILE adapter:</span></span>  
  
```  
objReceiveLocation["CustomCfg"] =   
        @"<CustomProps>"  
        + @"<BatchSize>20</BatchSize>"  
        + @"<FileMask>*.xml</FileMask>"  
        + @"<FileNetFailRetryCount>5</FileNetFailRetryCount>"  
        + @"<FileNetFailRetryInt>5</FileNetFailRetryInt>"  
        + @"</CustomProps>";  
```  
  
 <span data-ttu-id="fb369-117">在 CustomProps 項目內標記的名稱，就是配接器會用於這些屬性的內部名稱。</span><span class="sxs-lookup"><span data-stu-id="fb369-117">The names of the tags in the CustomProps element are the internal names that the adapter uses for the properties.</span></span>  
  
 <span data-ttu-id="fb369-118">MSMQ 配接器在 CustomProps 標記中設有單一個 AdapterConfig 標記。</span><span class="sxs-lookup"><span data-stu-id="fb369-118">The MSMQ adapter has a single tag, AdapterConfig, inside the CustomProps tag.</span></span> <span data-ttu-id="fb369-119">AdapterConfig 標記包含已括在 Config 標記中之自訂屬性值會使用的 XML 標記字串。</span><span class="sxs-lookup"><span data-stu-id="fb369-119">The AdapterConfig tag contains a string of XML tags for the custom property values enclosed in a Config tag.</span></span> <span data-ttu-id="fb369-120">不過，標記會編碼:"&lt;"取代"\<"和"&gt;"取代"\>"。</span><span class="sxs-lookup"><span data-stu-id="fb369-120">However, the tags are encoded: "&lt;" replaces "\<" and "&gt;" replaces "\>".</span></span> <span data-ttu-id="fb369-121">例如，用於 MSMQ 屬性之配接器子集的 XML 可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="fb369-121">For example, the XML for a subset of the adapter for MSMQ properties might appear as follows:</span></span>  
  
```  
<Config>  
    <batchSize>40</batchSize>  
</Config>  
```  
  
 <span data-ttu-id="fb369-122">請注意， **vt**屬性不是。</span><span class="sxs-lookup"><span data-stu-id="fb369-122">Notice that the **vt** attribute is not used.</span></span> <span data-ttu-id="fb369-123">指派給字串**CustomCfg**屬性編碼後顯示如下：</span><span class="sxs-lookup"><span data-stu-id="fb369-123">The string assigned to the **CustomCfg** property appears as follows after encoding:</span></span>  
  
```  
<CustomProps><AdapterConfig vt="8"><Config><batchSize>40</batchSize></Config></AdapterConfig></CustomProps>  
```  
  
## <a name="custom-property-names"></a><span data-ttu-id="fb369-124">自訂屬性名稱</span><span class="sxs-lookup"><span data-stu-id="fb369-124">Custom Property Names</span></span>  
 <span data-ttu-id="fb369-125">下表描述的 MSMQ 配接器的內部名稱**傳送**自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="fb369-125">The following table describes the internal names of the MSMQ adapter **Send** custom properties.</span></span>  
  
|<span data-ttu-id="fb369-126">**傳送自訂屬性名稱**</span><span class="sxs-lookup"><span data-stu-id="fb369-126">**Send custom property name**</span></span>|<span data-ttu-id="fb369-127">**顯示名稱**</span><span class="sxs-lookup"><span data-stu-id="fb369-127">**Display name**</span></span>|  
|-----------------------------------|----------------------|  
|<span data-ttu-id="fb369-128">acknowledgeType</span><span class="sxs-lookup"><span data-stu-id="fb369-128">acknowledgeType</span></span>|<span data-ttu-id="fb369-129">通知類型</span><span class="sxs-lookup"><span data-stu-id="fb369-129">Acknowledgement Type</span></span>|  
|<span data-ttu-id="fb369-130">administrationQueue</span><span class="sxs-lookup"><span data-stu-id="fb369-130">administrationQueue</span></span>|<span data-ttu-id="fb369-131">管理佇列</span><span class="sxs-lookup"><span data-stu-id="fb369-131">Administration Queue</span></span>|  
|<span data-ttu-id="fb369-132">憑證 (certificate)</span><span class="sxs-lookup"><span data-stu-id="fb369-132">certificate</span></span>|<span data-ttu-id="fb369-133">憑證指紋</span><span class="sxs-lookup"><span data-stu-id="fb369-133">Certificate Thumbprint</span></span>|  
|<span data-ttu-id="fb369-134">encryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="fb369-134">encryptionAlgorithm</span></span>|<span data-ttu-id="fb369-135">加密演算法</span><span class="sxs-lookup"><span data-stu-id="fb369-135">Encryption Algorithm</span></span>|  
|<span data-ttu-id="fb369-136">maximumMessageSize</span><span class="sxs-lookup"><span data-stu-id="fb369-136">maximumMessageSize</span></span>|<span data-ttu-id="fb369-137">訊息大小上限 (以 KB 為單位)</span><span class="sxs-lookup"><span data-stu-id="fb369-137">Maximum Message Size (in KB)</span></span>|  
|<span data-ttu-id="fb369-138">密碼</span><span class="sxs-lookup"><span data-stu-id="fb369-138">password</span></span>|<span data-ttu-id="fb369-139">密碼</span><span class="sxs-lookup"><span data-stu-id="fb369-139">Password</span></span>|  
|<span data-ttu-id="fb369-140">priority</span><span class="sxs-lookup"><span data-stu-id="fb369-140">priority</span></span>|<span data-ttu-id="fb369-141">訊息優先順序</span><span class="sxs-lookup"><span data-stu-id="fb369-141">Message Priority</span></span>|  
|<span data-ttu-id="fb369-142">queue</span><span class="sxs-lookup"><span data-stu-id="fb369-142">queue</span></span>|<span data-ttu-id="fb369-143">目的地佇列</span><span class="sxs-lookup"><span data-stu-id="fb369-143">Destination Queue</span></span>|  
|<span data-ttu-id="fb369-144">recoverable</span><span class="sxs-lookup"><span data-stu-id="fb369-144">recoverable</span></span>|<span data-ttu-id="fb369-145">可復原</span><span class="sxs-lookup"><span data-stu-id="fb369-145">Recoverable</span></span>|  
|<span data-ttu-id="fb369-146">segmentationSupport</span><span class="sxs-lookup"><span data-stu-id="fb369-146">segmentationSupport</span></span>|<span data-ttu-id="fb369-147">支援分割</span><span class="sxs-lookup"><span data-stu-id="fb369-147">Support Segmentation</span></span>|  
|<span data-ttu-id="fb369-148">sendBatchSize</span><span class="sxs-lookup"><span data-stu-id="fb369-148">sendBatchSize</span></span>|<span data-ttu-id="fb369-149">批次大小</span><span class="sxs-lookup"><span data-stu-id="fb369-149">Batch Size</span></span>|  
|<span data-ttu-id="fb369-150">sendQueueName</span><span class="sxs-lookup"><span data-stu-id="fb369-150">sendQueueName</span></span>|<span data-ttu-id="fb369-151">目的地佇列</span><span class="sxs-lookup"><span data-stu-id="fb369-151">Destination Queue</span></span>|  
|<span data-ttu-id="fb369-152">timeOut</span><span class="sxs-lookup"><span data-stu-id="fb369-152">timeOut</span></span>|<span data-ttu-id="fb369-153">逾時</span><span class="sxs-lookup"><span data-stu-id="fb369-153">Timeout</span></span>|  
|<span data-ttu-id="fb369-154">timeOutUnits</span><span class="sxs-lookup"><span data-stu-id="fb369-154">timeOutUnits</span></span>|<span data-ttu-id="fb369-155">逾時單位</span><span class="sxs-lookup"><span data-stu-id="fb369-155">Timeout Unit</span></span>|  
|<span data-ttu-id="fb369-156">transactional</span><span class="sxs-lookup"><span data-stu-id="fb369-156">transactional</span></span>|<span data-ttu-id="fb369-157">異動</span><span class="sxs-lookup"><span data-stu-id="fb369-157">Transactional</span></span>|  
|<span data-ttu-id="fb369-158">useAuthentication</span><span class="sxs-lookup"><span data-stu-id="fb369-158">useAuthentication</span></span>|<span data-ttu-id="fb369-159">使用驗證</span><span class="sxs-lookup"><span data-stu-id="fb369-159">Use Authentication</span></span>|  
|<span data-ttu-id="fb369-160">useDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="fb369-160">useDeadLetterQueue</span></span>|<span data-ttu-id="fb369-161">使用無法寄出的信件佇列</span><span class="sxs-lookup"><span data-stu-id="fb369-161">Use Dead Letter Queue</span></span>|  
|<span data-ttu-id="fb369-162">useJournalQueue</span><span class="sxs-lookup"><span data-stu-id="fb369-162">useJournalQueue</span></span>|<span data-ttu-id="fb369-163">使用日誌佇列</span><span class="sxs-lookup"><span data-stu-id="fb369-163">Use Journal Queue</span></span>|  
|<span data-ttu-id="fb369-164">userName</span><span class="sxs-lookup"><span data-stu-id="fb369-164">userName</span></span>|<span data-ttu-id="fb369-165">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="fb369-165">User Name</span></span>|  
  
 <span data-ttu-id="fb369-166">下表描述的 MSMQ 配接器的內部名稱**接收**自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="fb369-166">The following table describes the internal names of the MSMQ adapter **Receive** custom properties.</span></span>  
  
|<span data-ttu-id="fb369-167">**Receive 自訂屬性名稱**</span><span class="sxs-lookup"><span data-stu-id="fb369-167">**Receive custom property name**</span></span>|<span data-ttu-id="fb369-168">**顯示名稱**</span><span class="sxs-lookup"><span data-stu-id="fb369-168">**Display name**</span></span>|  
|--------------------------------------|----------------------|  
|<span data-ttu-id="fb369-169">batchSize</span><span class="sxs-lookup"><span data-stu-id="fb369-169">batchSize</span></span>|<span data-ttu-id="fb369-170">批次大小</span><span class="sxs-lookup"><span data-stu-id="fb369-170">Batch Size</span></span>|  
|<span data-ttu-id="fb369-171">密碼</span><span class="sxs-lookup"><span data-stu-id="fb369-171">Password</span></span>|<span data-ttu-id="fb369-172">密碼</span><span class="sxs-lookup"><span data-stu-id="fb369-172">Password</span></span>|  
|<span data-ttu-id="fb369-173">佇列</span><span class="sxs-lookup"><span data-stu-id="fb369-173">Queue</span></span>|<span data-ttu-id="fb369-174">佇列</span><span class="sxs-lookup"><span data-stu-id="fb369-174">Queue</span></span>|  
|<span data-ttu-id="fb369-175">serialProcessing</span><span class="sxs-lookup"><span data-stu-id="fb369-175">serialProcessing</span></span>|<span data-ttu-id="fb369-176">連續處理</span><span class="sxs-lookup"><span data-stu-id="fb369-176">Serial Processing</span></span>|  
|<span data-ttu-id="fb369-177">異動</span><span class="sxs-lookup"><span data-stu-id="fb369-177">Transactional</span></span>|<span data-ttu-id="fb369-178">異動</span><span class="sxs-lookup"><span data-stu-id="fb369-178">Transactional</span></span>|  
|<span data-ttu-id="fb369-179">userName</span><span class="sxs-lookup"><span data-stu-id="fb369-179">userName</span></span>|<span data-ttu-id="fb369-180">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="fb369-180">User Name</span></span>|  
  
## <a name="sample-code"></a><span data-ttu-id="fb369-181">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="fb369-181">Sample Code</span></span>  
 <span data-ttu-id="fb369-182">以下 C# 程式會針對 MSMQ 配接器建立單一個接收位置。</span><span class="sxs-lookup"><span data-stu-id="fb369-182">The following C# program creates a single receive location for the MSMQ adapter.</span></span> <span data-ttu-id="fb369-183">它會假設接收埠 ReceivePort1 存在，並且使用 Helper 函式來將這些自訂屬性編碼和格式化。</span><span class="sxs-lookup"><span data-stu-id="fb369-183">It assumes that the receive port, ReceivePort1, exists and uses a helper function to encode and format the custom properties.</span></span>  
  
```  
using System;  
using System.Management;  
using System.Text;  
  
namespace CreateReceive  
{  
    ///   
    /// Program to create a receive location.  
    ///   
    class CreateReceive  
    {  
        /// The main entry point for the application.  
  
        [STAThread]  
        static void Main()  
        {  
            // Custom properties & values  
            string cfg =   
                    @"<queue>FORMATNAME:DIRECT=OS:MYMACHINE02\PRIVATE$\QUEUE2</queue>"  
                    + @"<batchSize>40</batchSize>"  
                    + @"<transactional>true</transactional>"  
                    + @"<serialProcessing>false</serialProcessing>";  
  
            CreateReceiveLocation (  
                    "Code Created Location",  
                    "ReceivePort1",  
                    "MSMQ",  
                    "BizTalkServerApplication",  
                    EncodeCustomProps(cfg),  // Encode the custom props  
                    "Microsoft.BizTalk.DefaultPipelines.PassThruReceive,"   
                            + " Microsoft.BizTalk.DefaultPipelines,"   
                            + " Version=3.0.1.0, Culture=neutral,"   
                            + " PublicKeyToken=31bf3856ad364e35",  
                    @"FORMATNAME:DIRECT=OS:MYMACHINE\PRIVATE$\QUEUE2"  
                );  
  
        }  
  
        static string EncodeCustomProps (string cp) {  
  
            // Enclose the properties and values in a Config> tag.  
            StringBuilder tmp = new StringBuilder( @"<Config>" + cp + @"</Config>");  
  
            // Encode the string  
            tmp = tmp.Replace("<","<");  
            tmp = tmp.Replace(">",">");  
  
            return (  
                // Enclose the encoded string with necessary tags  
                "<CustomProps><AdapterConfig vt=\"8\">"  
                + tmp.ToString()   
                + "</AdapterConfig></CustomProps>");  
  
        }  
  
        static void CreateReceiveLocation (  
            string name,            // Location name  
            string port,            // Receive port, already exists  
            string adapterName,     // The transport type  
            string hostName,        // BTS host  
            string customCfg,       // Encoded custom properties  
            string pipeline,        // Full specification of pipeline  
            string inboundTransport)// Inbound transport url  
        {  
            try   
            {  
                // Create options to store options in management object  
                PutOptions options = new PutOptions();  
                options.Type = PutType.CreateOnly;  
  
                // Create a management object  
                // Get the class  
                ManagementClass objReceiveLocationClass =   
                           new ManagementClass(  
                               "root\\MicrosoftBizTalkServer",   
                               "MSBTS_ReceiveLocation",   
                               null);  
                // Create an instance of the member of the class  
                ManagementObject objReceiveLocation =  
                          objReceiveLocationClass.CreateInstance();  
  
                // Fill in the properties  
                objReceiveLocation["Name"] = name;  
                objReceiveLocation["ReceivePortName"] = port;  
                objReceiveLocation["AdapterName"] = adapterName;  
                objReceiveLocation["HostName"] = hostName;  
                objReceiveLocation["PipelineName"] = pipeline;  
                objReceiveLocation["CustomCfg"] = customCfg;  
                objReceiveLocation["IsDisabled"] = true;  
                objReceiveLocation["InBoundTransportURL"] = inboundTransport;  
  
                // Put the options -- creates the receive location  
                objReceiveLocation.Put(options);  
            }  
            catch (Exception excep)  
            {  
                System.Console.WriteLine("Create Receive Location ({0}) failed - {1}",  
                                                name, excep.Message);  
            }  
        }  
    }  
}  
```