## 클라우드 서버 FreeTier 성능 측정

> 작성자: 전도현(IMRaccoon)

### 환경

- Ubuntu 18.04
- Benchmark Script: https://github.com/n-st/nench

<br />

### Free Tier 타입 및 Specification

#### AWS

- type: t2.micro
- cpu: vCPU 1, Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz 1 core
- memory: 1GiB(983M), 2399.859 MHz

#### Azure

- type: B1S
- cpu: vCPU 1, Intel(R) Xeon(R) CPU E5-2673 v4 @ 2.30GHz 1 core
- memory: 1GiB(922M), 2294.687 MHz

#### Google Cloud Platform

- type: f1-micro
- cpu: vCPU 1, Intel(R) Xeon(R) CPU @ 2.30GHz 1 core
- memory: 0.6 GB(581M), 2300.000 MHz

#### Naver Cloud Platform

- type: micro
- cpu: vCPU 1, Intel(R) Xeon(R) CPU E5-2670 v3 @ 2.30GHz 1 core
- memory: 1GB(975M), 2300.039 MHz

<br />

### Performance

| 테스트 항목                    | AWS           | Azure         | GCP           | NCP           |
| ------------------------------ | ------------- | ------------- | ------------- | ------------- |
| **CPU**                        |
| SHA256-hashing 500 MB          | 3.282 seconds | 3.527 seconds | 3.259 seconds | 3.613 seconds |
| bzip2-compressing 500 MB       | 5.570 seconds | 5.900 seconds | 5.633 seconds | 5.816 seconds |
| AES-encrypting 500 MB          | 1.663 seconds | 1.759 seconds | 1.280 seconds | 1.998 seconds |
| **dd: sequential write speed** |
| 1st run                        | 64.66 MiB/s   | 17.07 MiB/s   | 35.76 MiB/s   | 4.01 MiB/s    |
| 2nd run                        | 61.32 MiB/s   | 17.07 MiB/s   | 35.86 MiB/s   | 3.62 MiB/s    |
| 3rd run                        | 61.13 MiB/s   | 17.07 MiB/s   | 35.86 MiB/s   | 3.72 MiB/s    |
| average                        | 62.37 MiB/s   | 17.07 MiB/s   | 35.83 MiB/s   | 3.78 MiB/s    |

참고

- https://blog.51sec.org/2019/03/free-tier-vps-bench-comparison-for-aws.html
